<template>
<div>
  <div v-bind:key="rep.id" v-for="rep in reps">
    <SingleRep v-bind:rep="rep" />
  </div>
</div>
</template>

<script>
import SingleRep from './SingleRep.vue'

export default {
  name: "Reps",
  components: {
    SingleRep
  },
  props: ["reps"]
}
</script>

<style scoped>

</style>
