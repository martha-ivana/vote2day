<template>
  <div id="app">
    <SearchBar v-on:find-districts="findDistricts" />
    <div v-if="hasData">
      <h3>You are within the following voting districts...</h3>
      <Divisions v-bind:divisions="divisions"/>
      <h3>Your polling site is...</h3>
      <div v-if="this.pollingLocations.address" class="polling-location">
        <h1>{{ this.pollingLocations.address.locationName }} </h1>
        <h2>{{ this.pollingLocations.address.line1 }}
        <br/>{{ this.pollingLocations.address.city }}, {{ this.pollingLocations.address.state }} {{ this.pollingLocations.address.zip }}</h2>
      </div>
      <h3>Your current representatives are...</h3>
      <Districts v-bind:districts="districts"/>
    </div>
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
      offices: [],
      pollingLocations: []
    }
  },
  computed: {
    hasData () {
      return this.divisions.length || this.districts.length || this.offices.length || this.pollingLocations.length
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
        // hard code second senator title...
        this.districts[3].office = this.offices[2]
      })
      axios.get(`https://www.googleapis.com/civicinfo/v2/voterinfo?address=${address}&electionId=2000&key=AIzaSyB76-kRbeKceg0YVbbHLXRErMC_eJI4dR8`)
      .then(res => {
        this.pollingLocations = res.data.pollingLocations ? res.data.pollingLocations[0] : [];
      })
      // eslint-disable-next-line no-console
      .catch(err => console.error(err))
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
  .polling-location {
  background-color: #931621;
  color: #edddd4;
}
</style>
