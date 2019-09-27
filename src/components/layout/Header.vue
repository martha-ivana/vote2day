<template>
  <header class="header">
    <h1>vote2day</h1>
    <div id="nav">
      <!-- <router-link to="/">home</router-link> -->
      <!-- <router-link to="/signup">sign up</router-link>
      <router-link to="/login">log in</router-link> -->
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
    text-align: center;
    padding: 10px;
  }

  #nav {
    display: flex;
    justify-content: space-between;
  }
</style>
