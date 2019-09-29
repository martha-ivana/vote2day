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
import Divisions from '../components/Divisions';
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
          // connect offices to representatives
          for (let i = 0; i < this.offices.length; i++) {
            for (let j = 0; j < this.districts.length; j++) {
              if (this.offices[i].officialIndices[0] === j) {
                this.districts[j].office = this.offices[i]
              }
            }
          }
          // hard coding second senators title
          this.districts[3].office = this.offices[2]
        })
        .catch(err => console.log(err))
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
  
  a {
    color: #fff;
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
