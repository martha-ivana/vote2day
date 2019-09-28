<template>
  <div>
    <form @submit.prevent="findDistricts">
      <input type="text" v-model="address" name="address" placeholder="enter your zipcode OR for more accurate results, your full street address with city, state, and zipcode [ e.g. 308 Hooper St, Brooklyn, NY 11211 ]">
      <input type="submit" value="search" class="btn">
    </form>
  </div>
</template>

<script>
import uuid from 'uuid';
export default {
  name: "SearchBar",
  data() {
    return {
      address: ''
    }
  },
  methods: {
    findDistricts() {
      const newAddress = {
        id: uuid.v4(),
        address: this.address
      }
      const inputAddress = newAddress.address
      this.$emit('find-districts', inputAddress);

      this.address = ''
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
