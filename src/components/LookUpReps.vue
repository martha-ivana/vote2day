<template>
  <div>
    <form>
      <input type="number" name="zipcode" placeholder="Enter your zipcode">
      <input type="submit" value="search" class="btn">
    </form>
  </div>
</template>

<script>
export default {
  name: "LookUpReps"
}
</script>

<style scoped>
  form {
    display: flex;
  }

  input[type="number"] {
    flex: 10;
    padding: 5px;
  }

  input[type="submit"] {
    flex: 2;
  }
</style>
