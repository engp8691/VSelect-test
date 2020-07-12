<template>
  <v-select
    label="label"
    :options="options"    
    :clearable="false"
    :placeholder="placeHolder"
    :value="selectedValue"
    @input="selectHandle"
  />
</template>

<script>
import Vue from "vue";
import vSelect from "vue-select";
import "vue-select/dist/vue-select.css";

Vue.component("v-select", vSelect);

export default {
  data: () => ({
    selectedValue: null
  }),

  props: {
    currentValue: [Number, String, Object],
    placeHolder: String,
    options: Array
  },

  mounted() {
    this.selectedValue = this.currentValue;
  },

  methods: {
    selectHandle(e) {
      this.selectedValue = e;
      this.$emit("onSelect", {
        placeHolder: this.placeHolder,
        selectedValue: this.selectedValue
      });
    }
  }
};
</script>
