<template>
  <div>
    <div v-bind:key="bill.name" v-for="bill in senateBills">
      <SingleBill v-bind:bill="bill" />
    </div>
  </div>
</template>

<script>
import SingleBill from './SingleBill.vue';

export default {
  name: "SenateBills",
  components: {
    SingleBill
  },
  props: ["senateBills"]
}
</script>

<style scoped>
</style>
