<template>
  <div>
    <h2 class="elections-title">These elections are coming up...</h2>
    <div v-bind:key="election.id" v-for="election in elections">
      <SingleElection v-bind:election="election"/>
    </div>
  </div>
</template>

<script>
import SingleElection from './SingleElection.vue';
import axios from 'axios';
import moment from 'moment';

export default {
  name: "Elections",
  components: {
    SingleElection,
  },
  data() {
    return {
      elections: []
    }
  },
  created: function() {
    axios.get(`https://www.googleapis.com/civicinfo/v2/elections?alt=json&prettyPrint=true&key=AIzaSyCLMVdSf6hH5w1QvbYt1PNS1hNFheRiz40`)
    .then(res => {
      this.elections = res.data.elections
      this.elections.forEach(election => 
        election.timeFromNow = moment(election.electionDay).endOf('day').fromNow()
      )
    })
    .catch(err => console.log(err))
  }
}
</script>

<style scoped>
.elections-title {
  background-color: #931621;
  color: #edddd4;
}
</style>
