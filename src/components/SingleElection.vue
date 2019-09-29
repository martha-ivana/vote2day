<template>
  <div class="single-election">
      <h2>{{ election.name }} </h2>
      <p>taking place {{ election.timeFromNow }} on {{ election.electionDay }}</p>
  </div>
</template>

<script>
export default {
  name: "SingleElection",
  props: ["election"],
}
</script>

<style scoped>
  
  a {
    color: #931621;
  }
  a:visited {
    color: #0b4f6c;
  }
  h2 {
    color: #0b4f6c;
  }
  .office {
    color: #0b4f6c;
  }
  .single-election {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 2px #c44536 dotted;
    justify-content: space-between;
  }
</style>
