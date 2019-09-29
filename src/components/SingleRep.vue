<template>
  <div class="single-rep">
      <h3>{{ district.name }}</h3>
      <div v-if="district.office">
        ★ {{ district.office.name }} ★
      </div>
      <div v-if="district.phones">
        <sub> ★ {{ district.phones[0] }} ★ </sub>
      </div>
      <div v-if="district.emails">
        <sub> ★ {{ district.emails[0] }} ★ </sub>
      </div>
  </div>
</template>

<script>
export default {
  name: "SingleRep",
  props: ["district"],
}
</script>

<style scoped>

  h3 {
    color: #0b4f6c;
  }
  
  .single-rep {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 2px #c44536 dotted;
    justify-content: space-between;
  }
</style>
