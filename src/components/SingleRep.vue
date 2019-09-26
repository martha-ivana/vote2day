<template>
  <div class="single-rep">
    <p>{{rep.name}}</p>
  </div>
</template>

<script>
export default {
  name: "SingleRep",
  props: ["rep"]
}
</script>

<style scoped>
  .single-rep {
    background: lavender;
    padding: 10px;
    border-bottom: 1px coral dotted;
  }
</style>
