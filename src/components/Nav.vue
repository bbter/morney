<template>
  <div class="nav">
    <RouterLink to="/money">
      <Icon name="money"/>
      记账
    </RouterLink>
    |
    <RouterLink to="/labels">
      <Icon name="labels"/>
      标签
    </RouterLink>
    |
    <RouterLink to="/statistics">
      <Icon name="statistics"/>
      统计
    </RouterLink>
  </div>
</template>

<script lang="ts">
export default {
  name: 'Nav'
};
</script>

<style lang="scss" scoped>
.nav {
  border: 1px solid red;
}
</style>