<template>
  <div>
    <div id="instructions">enter your address to find your voting districts, polling site and current representatives</div>
    <form @submit.prevent="findDistricts">
      <input type="text" v-model="address.buildingNumber" name="buildingNumber" placeholder="building #"/>
      <input type="text" v-model="address.street" name="street" placeholder="street"/>
      <input type="text" v-model="address.city" name="city" placeholder="city"/>
      <input type="text" v-model="address.state" name="state" placeholder="state"/>
      <input type="text" v-model="address.zipcode" name="zipcode" placeholder="zipcode"/>
      <input type="submit" value="search" class="btn"/>
    </form>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      address: {
        buildingNumber: '',
        street: '',
        city: '',
        state: '',
        zipcode: ''
      },
    };
  },
  methods: {
    findDistricts() {
      this.$emit("find-districts", Object.values(this.address).join(' '));
      this.address = {};
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  justify-content: space-between;
}
input[type="text"] {
  flex: 10;
  padding: 10px;
  border-width: 1px;
  border-color: -internal-light-dark(black, white);
}
input[type="submit"] {
  flex: 2;
  border-radius: 0px;
  -webkit-border-radius: 0px;
}
input,
textarea {
  -webkit-appearance: none;
  border-radius: 0;
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
  background: #333;
}
#instructions {
  color: #931621;
  font-weight: bold;
  width: 100%;
  padding: 10px;
  font-size: 1rem;
}
@media only screen and (max-width: 768px) {
  form {
    display: inline-block;
  }
  input {
    width: 100%;
  }
  .btn {
    width: 100%;
  }
}
</style>
