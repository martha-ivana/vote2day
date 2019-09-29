<template>
  <div class="single-bill">
      <h3>{{ bill.number }} </h3>
      <h3>{{ bill.primary_subject }}</h3>
      <sub>introduced on {{ bill.introduced_date }}</sub>
      <br><sub><b>last major action</b>: {{ bill.latest_major_action }} <b>{{ bill.timeFromNow }}</b></sub>
      <br>★ <b><a v-bind:href="bill.govtrack_url">read more about this bill on govtrack.us</a></b> ★ 
  </div>
</template>

<script>
export default {
  name: "SingleBill",
  props: ["bill"],
}
</script>

<style scoped>
  
  a {
    color: #931621;
  }
  a:visited {
    color: #0b4f6c;
  }
  h3 {
    color: #0b4f6c;
  }
  .office {
    color: #0b4f6c;
  }
  .single-bill {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 2px #c44536 dotted;
    justify-content: space-between;
  }
</style>
