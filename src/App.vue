<template>
  <div>
    <router-view />
    <hr>
    <div>
      <RouterLink to="/money" >记账</RouterLink>
      |
      <RouterLink to="/labels" >标签</RouterLink>
      |
      <RouterLink to="/statistics">统计</RouterLink>
    </div>
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
