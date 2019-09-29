<template>
  <div>
    <div v-bind:key="bill.name" v-for="bill in searchResults">
      <SingleBill v-bind:bill="bill" />
    </div>
  </div>
</template>

<script>
import SingleBill from './SingleBill.vue';

export default {
  name: "SearchBills",
  components: {
    SingleBill
  },
  props: ["searchResults"]
}
</script>

<style scoped>
</style>
