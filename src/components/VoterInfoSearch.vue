<template>
  <div>
    <form @submit.prevent="findVoterInfo">
      <input type="text" v-model="address" name="address" placeholder="enter your zipcode OR for more accurate results, your full street address with city, state, and zipcode [ e.g. 308 Hooper St, Brooklyn, NY 11211 ]">
      <input type="submit" value="search" class="btn">
    </form>
  </div>
</template>

<script>
export default {
  name: "VoterInfoSearch",
  data() {
    return {
      address: ''
    }
  },
  methods: {
    findVoterInfo() {
      this.$emit('find-voter-info', this.address);
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
