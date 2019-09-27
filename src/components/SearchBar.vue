<template>
  <div>
    <form @submit.prevent="findDistricts">
      <input type="text" v-model="address" name="address" placeholder="enter your zipcode or, for more accurate results, your full street address">
      <input type="submit" value="search" class="btn">
    </form>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      name: '',
      address: ''
    }
  },
  methods: {
    findDistricts() {
      const district = {
        name: this.name,
        address: this.address,
        number: this.number,
      }
      this.$emit('find-districts', district);
      this.name = '';
      this.address = '';
      this.number;
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
  background: #392f5a;
}
</style>
