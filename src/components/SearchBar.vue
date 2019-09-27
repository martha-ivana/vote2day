<template>
  <div>
    <form @submit.prevent="findDistricts">
      <input type="text" v-model="address" name="address" placeholder="enter your zipcode or, for more accurate results, your full street address">
      <input type="submit" value="Submit" class="btn">
    </form>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      address: ''
    }
  },
  methods: {
    findDistricts() {
      const district = {
        address: this.address
      }
      this.$emit('find-districts', district);
      this.address = '';
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
