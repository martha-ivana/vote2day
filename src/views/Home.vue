<template>
  <div id="app">
    <SearchBar v-on:find-districts="findDistricts" />
    <Districts v-bind:districts="districts" v-on:rem-district="removeDistrict" />
  </div>
</template>

<script>
import Districts from '../components/Districts';
import SearchBar from '../components/SearchBar';
import axios from 'axios';
export default {
  name: 'Home',
  components: {
    Districts,
    SearchBar
  },
  data() {
    return {
      districts: []
    }
  },
  methods: {
    removeDistrict(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${number}`)
        .then(res => this.districts = this.districts.filter(district => district.number !== number))
        .catch(err => console.log(err));
    },
    findDistricts(address) {
      axios.get(`https://api.geocod.io/v1.4/geocode?q=${address}&fields=cd&api_key=8d9534882ad3d344da9242ada848d5574a88a99`)
        .then(res => this.districts = res.data)
        .catch(err => console.log(err));
    }
  },
  // created() {
  //   axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
  //     .then(res => this.todos = res.data)
  //     .catch(err => console.log(err));
  // }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
  .btn {
    border: none;
    background: #555;
    color: #fff;
    cursor: pointer;
    display: inline-block;
    font-size: 20px;
    padding: 7px 20px;
  }
  .btn:hover {
    background: #666;
  }
</style>
