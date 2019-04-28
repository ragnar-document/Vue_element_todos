<template>
  <div id="app">
    <router-link to="/">Home</router-link>
    <router-view></router-view>
  </div>
</template>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
html{
  height: 100%;
  background: #4997e4;
}

</style>
