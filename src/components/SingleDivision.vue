<template>
  <div class="single-division">
      <h4>{{ division.name }}</h4>
  </div>
</template>

<script>
export default {
  name: "SingleDivision",
  props: ["division"],
}
</script>

<style scoped>

  h4 {
    color: #c44f36;
  }
  
  .single-division {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 2px #c44536 dotted;
    justify-content: space-between;
  }
  .is-selected {
    text-decoration: underline;
  }
</style>
