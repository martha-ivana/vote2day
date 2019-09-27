<template>
  <div id="app">
    <Header/>
    <router-view/>
  </div>
</template>

<script>
import Header from './components/layout/Header.vue'
export default {
  name: "app",
  components: {
    Header
  }
}
</script>

<style>
#app {
  background-color: #edddd4;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}

a {
  color: #fff;
  text-decoration: none;
}

a:visited {
  color: #888;
  text-decoration: none;
}

a:hover {
  text-decoration: none;
}

* {
  margin: 0px;
}

</style>
