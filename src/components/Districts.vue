<template>
  <div>
    <div v-bind:key="district.number" v-for="district in districts">
      <SingleRep v-bind:district="district" />
    </div>
  </div>
</template>

<script>
import SingleRep from './SingleRep.vue';

export default {
  name: "Districts",
  components: {
    SingleRep
  },
  props: ["districts"]
}
</script>

<style scoped>
</style>
