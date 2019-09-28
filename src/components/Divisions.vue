<template>
  <div>
    <div v-bind:key="division.id" v-for="division in divisions">
      <SingleDivision v-bind:division="division" />
    </div>
  </div>
</template>

<script>
import SingleDivision from './SingleDivision.vue';

export default {
  name: "Divisions",
  components: {
    SingleDivision
  },
  props: ["divisions"]
}
</script>

<style scoped>
</style>
