<template>
  <div>
    <SearchForBills v-on:find-bills="findBills" />
    <h3>These bills resulted from your search...</h3>
    <SearchBillsResult v-bind:searchResults="searchResults"/>
    
  </div>
</template>

<script>
import SearchBillsResult from './SearchBillsResult.vue';
import SearchForBills from './SearchForBills.vue';
import axios from 'axios';
import moment from 'moment';

let config = {'X-API-Key': 'IXoAMnNJe3fKvZXXgAD412lHfwbONJ5Kb6EGxIAN'}

export default {
  name: "Bills",
  components: {
    SearchBillsResult,
    SearchForBills
  },
  data() {
    return {
      searchResults: [],
    }
  },
  methods: {
    findBills(searchTerm) {
      axios.get(`https://api.propublica.org/congress/v1/bills/search.json?query=${searchTerm}`, {headers: config})
      .then(res => {
        this.searchResults = res.data.results[0].bills
        this.searchResults.forEach(bill => bill.timeFromNow = moment(bill.latest_major_action_date).endOf('day').fromNow())
      })
      .catch(err => console.log(err))
    }
  },
}
</script>

<style scoped>
.polling-location {
  background-color: #931621;
  color: #edddd4;
}
</style>
