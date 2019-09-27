<template>
  <div>
    <div v-bind:key="district.id" v-for="district in districts">
      <SingleDistrict v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
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
