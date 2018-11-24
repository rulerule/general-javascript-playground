<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style lang="scss">
body {
  height:100%;
  width:100%;
  margin:0;
  overflow:hidden;
}
html {
  height:100%;
  width:100%;
  overflow:hidden;
}

#app {
  width:100%;
  height:100%;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  overflow:hidden;
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
