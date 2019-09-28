<template>
<!-- if district is selected, bind it to the district.selected class -->
  <div class="single-district" v-bind:class="{'is-selected':district.selected}">
    <p>
      <input type="checkbox" v-on:change="selectDistrict" v-bind:checked="district.selected"> {{ district.name }} ★
    </p>
  </div>
</template>

<script>
export default {
  name: "SingleRep",
  props: ["district"],
  methods: {
    selectDistrict() {
      this.district.selected = !this.district.selected;
    }
  }
}
</script>

<style scoped>
  .single-district {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 2px #c44536 dotted;
    justify-content: space-between
  }
  .is-selected {
    text-decoration: underline;
  }
</style>
