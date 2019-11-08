<template>
  <div id="app">
    <Header/>
    <router-view/>
    <Footer/>
  </div>
</template>

<script>
import Header from './components/layout/Header.vue'
import Footer from './components/layout/Footer.vue'
export default {
  name: "app",
  components: {
    Header,
    Footer
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

@media only screen and (max-width: 414px) {
  body {
    font-size: 1em;
  }
  h1 {
    font-size: 2.5em;
  }
  a {
  font-size: .8em;
  font-weight: 500;
  }
  footer.footer {
    background-color: #edddd4;
    bottom: 0;
    position: absolute;
  }
}

</style>
