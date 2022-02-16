<script>
import VueMultiselect from "vue-multiselect";

export default {
  components: { VueMultiselect },
  data() {
    return {
      selected: null,
      options: ["list", "of", "options"],
    };
  },
};
</script>

<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h2>Example multi-select</h2>
    <VueMultiselect v-model="selected" :multiple="true" :options="options"></VueMultiselect>
    <h2>Example chart</h2>
    <line-chart :data="{ '2017-05-13': 2, '2017-05-14': 5 }"></line-chart>
    <pie-chart
      :data="[
        ['Blueberry', 44],
        ['Strawberry', 23],
      ]"
    ></pie-chart>
  </div>
</template>

<style src="vue-multiselect/dist/vue-multiselect.css"></style>
