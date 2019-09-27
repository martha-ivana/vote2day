<template>
  <div>
    <div v-bind:key="district.number" v-for="district in districts">
      <SingleDistrict v-bind:district="district" />
    </div>
  </div>
</template>

<script>
import SingleDistrict from './SingleDistrict.vue';

export default {
  name: "Districts",
  components: {
    SingleDistrict
  },
  props: ["districts"]
}
</script>

<style scoped>
</style>
