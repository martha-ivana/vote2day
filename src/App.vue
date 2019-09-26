<template>
  <div id="app">
    <img alt="vote2day logo" src="./assets/logo.png">
    <Header/>
    <LookUpReps/>
    <Introduction msg="Voice Your Vote"/>
  </div>
</template>

<script>
import Introduction from './components/Introduction.vue'
import Header from './components/Header.vue'
import LookUpReps from './components/LookUpReps.vue'

export default {
  name: 'app',
  components: {
    Header,
    Introduction
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

* {
  margin: 0;
}

.btn {
  display: inline-block;
  border: none;
  background: #333;
  color: #ffffff;
  padding: 7px 20px;
  cursor: pointer;
}

</style>
