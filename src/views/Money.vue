<template>
  <Layout class-prefix="layout">
    <NumberPad :value.sync="record.amount" @submit="saveRecord"/>
    <Tabs :data-source="recordTypeList"
          :value.sync="record.type"/>
    <div class="createdAt">
      <FormItem type="date" placeholder="在这里输入日期" field-name="日期" :value.sync="record.createdAt"/>
    </div>
    <div class="notes">
      <FormItem placeholder="在这里输入备注" field-name="备注" :value.sync="record.notes"/>
    </div>
    <Tags @update:value="record.tags = $event"/>
  </Layout>
</template>
<script lang="ts">

import NumberPad from '@/components/Money/NumberPad.vue';
import FormItem from '@/components/Money/FormItem.vue';
import Tags from '@/components/Money/Tags.vue';
import Vue from 'vue';
import {Component} from 'vue-property-decorator';
import recordTypeList from '@/constants/recordTypeList';
import Tabs from '@/components/Tabs.vue';

@Component({
  components: {Tabs, Tags, FormItem, NumberPad},
})
export default class Money extends Vue {
  get recordList() {
    return this.$store.state.recordList;
  }

  recordTypeList = recordTypeList;

  record: RecordItem = {tags: [], notes: '', type: '-', amount: 0, createdAt: new Date().toISOString()};

  created() {
    this.$store.commit('fetchRecords');
  }

  saveRecord() {
    if (this.record.tags.length === 0 || !this.record.tags) {
      return window.alert('请至少选择一个标签');
    }
    this.$store.commit('createRecord', this.record);
    this.record.notes = '';
  }
}
</script>
<style lang="scss" scoped>
::v-deep .layout-content {
  display: flex;
  flex-direction: column-reverse;
}

.notes {
  padding-top: 12px;
}

</style>