<template>
  <header class="header">
    <h1>vote2day</h1>
    <div id="nav">
      <!-- <router-link to="/bills">upcoming votes</router-link> -->
      <router-link to="/">find your reps</router-link>
      <router-link to="/bills">search bills</router-link>
      <router-link to="/latest">latest bills</router-link>
      <router-link to="/elections">upcoming elections</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header"
}
</script>

<style scoped>
  .header {
    background: #0b4f6c;
    color: #ffffff;
    font-size: 28px;
    padding: 10px;
    text-align: center;
  }

  #nav {
    display: flex;
    justify-content: space-between;
  }
</style>
