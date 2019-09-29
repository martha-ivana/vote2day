<template>
  <div class="single-rep">
      <h2>{{ district.name }}</h2>
      <div v-if="district.office" class="office">
        {{ district.office.name }}
      </div>
      <div v-if="district.phones">
        <sub> ★ {{ district.phones[0] }} ★ </sub>
      </div>
      <div v-if="district.emails">
        <sub> ★ {{ district.emails[0] }} ★ </sub>
      </div>
      <sub> ★ <b><a v-bind:href="district.urls[0]">website</a></b> ★ </sub>
  </div>
</template>

<script>
export default {
  name: "SingleRep",
  props: ["district"],
}
</script>

<style scoped>
  
  a {
    color: #931621;
  }
  a:visited {
    color: #0b4f6c;
  }
  h2 {
    color: #0b4f6c;
  }
  .office {
    color: #0b4f6c;
  }
  .single-rep {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 2px #c44536 dotted;
    justify-content: space-between;
  }
</style>
