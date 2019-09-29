<template>
  <div>
    <VoterInfoSearch v-on:find-voter-info="findVoterInfo" />
    <h3>Your polling site is...</h3>
    <div v-if="this.pollingLocations.address" class="polling-location">
      <h2>{{ this.pollingLocations.address.locationName }} </h2>
      {{ this.pollingLocations.address.line1 }}
      <br/>{{ this.pollingLocations.address.city }}, {{ this.pollingLocations.address.state }} {{ this.pollingLocations.address.zip }}
    </div>
    <h3>These candidates are on your next ballot...</h3>
    <!-- <div v-bind:key="election.id" v-for="election in elections">
      <SingleElection v-bind:election="election"/>
    </div> -->
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
      ballots: [],
      pollingLocations: [],
    }
  },
  methods: {
    findVoterInfo(address) {
      axios.get(`https://www.googleapis.com/civicinfo/v2/voterinfo?address=${address}&electionId=2000&key=AIzaSyB76-kRbeKceg0YVbbHLXRErMC_eJI4dR8`)
      .then(res => {
        this.ballots = res.data.contests;
        this.pollingLocations = res.data.pollingLocations[0];
      })
      .catch(err => console.log(err))
    }
  }
}
</script>

<style scoped>
.polling-location {
  background-color: #931621;
  color: #edddd4;
}
</style>
