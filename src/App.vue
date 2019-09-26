<template>
  <div id="app">
    <!-- <img alt="vote2day logo" src="./assets/logo.png"> -->
    <Header/>
    <FindReps/>
    <Reps v-bind:reps="reps"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import FindReps from './components/FindReps.vue'
import Reps from './components/Reps.vue'

export default {
  name: 'app',
  components: {
    Header,
    FindReps,
    Reps
  },
  data() {
    return {
      reps: []
    }
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
