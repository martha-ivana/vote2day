<template>
  <div>
    <SearchForBills v-on:find-bills="findBills" />
    <h3>These bills resulted from your search...</h3>
    <SearchBills v-bind:searchResults="searchResults"/>
    <h3>These are the 20 most recently active bills in the Senate...</h3>
    <SenateBills v-bind:senateBills="senateBills"/>
    <h3>These are the 20 most recently active bills in the House...</h3>
    <HouseBills v-bind:houseBills="houseBills"/>
  </div>
</template>

<script>
import HouseBills from './HouseBills.vue';
import SenateBills from './SenateBills.vue';
import SearchBills from './SearchBills.vue';
import SearchForBills from './SearchForBills.vue';
import axios from 'axios';
import moment from 'moment';

let config = {'X-API-Key': 'IXoAMnNJe3fKvZXXgAD412lHfwbONJ5Kb6EGxIAN'}

export default {
  name: "Bills",
  components: {
    HouseBills,
    SenateBills,
    SearchBills,
    SearchForBills
  },
  data() {
    return {
      allBills: [],
      senateBills: [],
      houseBills: [],
      searchResults: [],
    }
  },
  methods: {
    findBills(searchTerm) {
      axios.get(`https://api.propublica.org/congress/v1/bills/search.json?query=${searchTerm}`, {headers: config})
      .then(res => this.searchResults = res.data.results[0].bills)
      .catch(err => console.log(err))
    }
  },
  created: function() {
    axios.get('https://api.propublica.org/congress/v1/116/both/bills/active.json', {headers: config})
    .then(res => this.allBills = res.data.results[0].bills)
    axios.get('https://api.propublica.org/congress/v1/116/house/bills/active.json', {headers: config})
    .then(res => this.houseBills = res.data.results[0].bills)
    axios.get('https://api.propublica.org/congress/v1/116/senate/bills/active.json', {headers: config})
    .then(res => this.senateBills = res.data.results[0].bills)
    .catch(err => console.log(err))
  }
}
</script>

<style scoped>
.polling-location {
  background-color: #931621;
  color: #edddd4;
}
</style>
