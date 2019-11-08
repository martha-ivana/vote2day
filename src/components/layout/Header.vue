<template>
  <header class="header">
    <h1>vote2day</h1>
    <div id="nav-toggle" @click="toggleMenu()">menu</div>
    <div id="nav" class="navbar">
      <router-link to="/">find your reps</router-link>
      <router-link to="/bills">search bills</router-link>
      <router-link to="/latest">see latest bills</router-link>
      <router-link to="/elections">find upcoming elections</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  methods: {
    toggleMenu: function(){ 
      let nav = document.getElementById("nav")
      let menu = document.getElementById("nav-toggle")
      if (nav.className === "navbar") {
        nav.className += "responsive"
        menu.innerHTML = "hide menu"
      } else {
        nav.className = "navbar"
        menu.innerHTML = "menu"
      }
    }
  }
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
  #nav-toggle {
    display: none;
  }
  @media only screen and (max-width: 768px) {
    #nav {
      flex-direction: column;
    }
    #nav-toggle {
      display: initial;
      cursor: pointer;
    }
    .navbar a {
      display: none;
    }
    .navbar.responsive a {
      font-size: 1.5em;
      float: none;
      display: block;
    }
  }
</style>
