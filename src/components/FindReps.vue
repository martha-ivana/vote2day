<template>
  <div>
    <form @submit="findReps">
      <input type="text" v-model="zipcode" name="zipcode" placeholder="Enter your zipcode">
      <input type="submit" value="search" class="btn">
    </form>
  </div>
</template>

<script>
export default {
  name: "FindReps",
  data() {
    return {
      zipcode: ''
    }
  },
  methods: {
    findReps() {
      const newToDo = {
        id: 1,
        zipcode: this.zipcode
      }
    // send up to parent
    this.$emit('add-todo', newToDo)
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
  }

  input[type="text"] {
    flex: 10;
    padding: 5px;
  }

  input[type="submit"] {
    flex: 2;
  }
</style>
