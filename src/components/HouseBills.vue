<template>
  <div>
    <div v-bind:key="bill.name" v-for="bill in houseBills">
      <SingleBill v-bind:bill="bill" />
    </div>
  </div>
</template>

<script>
import SingleBill from './SingleBill.vue';

export default {
  name: "HouseBills",
  components: {
    SingleBill
  },
  props: ["houseBills"]
}
</script>

<style scoped>
</style>
