<template>
  <div>
    <form @submit.prevent="findBills">
      <input type="text" v-model="searchTerm" name="searchTerm" placeholder="enter a search term to find bills that match the subject matter [ e.g. environment ]">
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
    border-radius: 0px;
    -webkit-border-radius: 0px;
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

input, textarea {
  -webkit-appearance: none;
  border-radius: 0;
}
</style>
