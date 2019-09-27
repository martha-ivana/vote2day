<template>
  <div class="single-district" v-bind:class="{'is-selected':district.selected}">
    <p>
      <input type="checkbox" v-on:change="selectDistrict" v-bind:checked="district.selected">
      {{district.name}}
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
      </p>
  </div>
</template>

<script>
export default {
  name: "SingleDistrict",
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
    border-bottom: 1px #ccc dotted;
  }
  .is-selected {
    text-decoration: underline;
  }
  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>
