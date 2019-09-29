<template>
  <div>
    <h3>The most recently active bills are listed below...</h3>
    <h2 class="bills-title">from the Senate...</h2>
      <SenateBills v-bind:senateBills="senateBills"/>
    <h2 class="bills-title">from the House...</h2>
      <HouseBills v-bind:houseBills="houseBills"/>
  </div>
</template>

<script>
import HouseBills from './HouseBills.vue';
import SenateBills from './SenateBills.vue';
import axios from 'axios';
import moment from 'moment';

let config = {'X-API-Key': 'IXoAMnNJe3fKvZXXgAD412lHfwbONJ5Kb6EGxIAN'}

export default {
  name: "LatestBills",
  components: {
    HouseBills,
    SenateBills,
  },
  data() {
    return {
      senateBills: [],
      houseBills: []
    }
  },
  created: function() {
    axios.get('https://api.propublica.org/congress/v1/116/house/bills/active.json', {headers: config})
    .then(res => {
      this.houseBills = res.data.results[0].bills
      this.houseBills.forEach(bill => bill.timeFromNow = moment(bill.latest_major_action_date).endOf('day').fromNow())
    })
    axios.get('https://api.propublica.org/congress/v1/116/senate/bills/active.json', {headers: config})
    .then(res => {
      this.senateBills = res.data.results[0].bills
      this.senateBills.forEach(bill => bill.timeFromNow = moment(bill.latest_major_action_date).endOf('day').fromNow())
    })
    .catch(err => console.log(err))
  }
}
</script>

<style scoped>
.bills-title {
  background-color: #931621;
  color: #edddd4;
}
</style>
