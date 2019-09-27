<template>
  <div>
    <div v-bind:key="district.id" v-for="district in districts">
      <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
    </div>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue';
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
