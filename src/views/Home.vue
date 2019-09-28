<template>
  <div id="app">
    <SearchBar v-on:find-districts="findDistricts" />
    <h3>You are within the following voting districts...</h3>
    <Divisions v-bind:divisions="divisions"/>
    <h3>Your representatives are...</h3>
    <Districts v-bind:districts="districts"/>
  </div>
</template>

<script>
import Divisions from '../components/Divisions'
import Districts from '../components/Districts';
import SearchBar from '../components/SearchBar';
import axios from 'axios';
export default {
  name: 'Home',
  components: {
    Divisions,
    Districts,
    SearchBar
  },
  data() {
    return {
      divisions: [],
      districts: [],
      offices: []
    }
  },
  methods: {
    findDistricts(address) {
      axios.get(`https://www.googleapis.com/civicinfo/v2/representatives?key=AIzaSyB76-kRbeKceg0YVbbHLXRErMC_eJI4dR8&address=${address}`)
        .then(res => {
          this.divisions = res.data.divisions
          this.districts = res.data.officials
          this.offices = res.data.offices
        })
        .catch(err => console.log(err))
      
      // const res = await axios.get(`https://api.geocod.io/v1.4/geocode?q=${address}&fields=cd&api_key=8d9534882ad3d344da9242ada848d5574a88a99`)
      //   .then(res => this.districts = res.data)
      //   .catch(err => console.log(err))
    }
  }
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
