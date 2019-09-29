<template>
  <div>
    <VoterInfoSearch v-on:find-voter-info="findVoterInfo" />
    <h3>Your polling site is...</h3>
    <h3>These candidates are on your next ballot...</h3>
    <div v-bind:key="election.id" v-for="election in elections">
      <SingleElection v-bind:election="election"/>
    </div>
  </div>
</template>

<script>
import VoterInfoSearch from './VoterInfoSearch.vue';
import SingleElection from './SingleElection.vue';
import axios from 'axios';
import moment from 'moment';


export default {
  name: "Elections",
  components: {
    SingleElection,
    VoterInfoSearch
  },
  data() {
    return {
      voterInfo: []
    }
  },
  methods: {
    findVoterInfo(address) {
      axios.get(`https://www.googleapis.com/civicinfo/v2/voterinfo?key=AIzaSyB76-kRbeKceg0YVbbHLXRErMC_eJI4dR8&address=${address}`)
      .catch(err => console.log(err))
    }
  }
}
</script>

<style scoped>
.elections-title {
  background-color: #931621;
  color: #edddd4;
}
</style>
