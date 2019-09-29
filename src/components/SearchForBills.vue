<template>
  <div>
    <form @submit.prevent="findBills">
      <input type="text" v-model="searchTerm" name="searchTerm" placeholder="enter a search term to find active bills that match [ e.g. environment ]">
      <input type="submit" value="search" class="btn">
    </form>
  </div>
</template>

<script>
export default {
  name: "SearchForBills",
  data() {
    return {
      searchTerm: ''
    }
  },
  methods: {
    findBills(searchTerm) {
      this.$emit('find-bills', this.searchTerm);
      this.searchTerm = ''
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
    padding: 10px;
  }
  input[type="submit"] {
    flex: 2;
  }

.btn {
  display: inline-block;
  border: none;
  background: #931621;
  color: #ffffff;
  padding: 10px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #333  ;
}
</style>
