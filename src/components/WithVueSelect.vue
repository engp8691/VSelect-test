<template>
  <v-select
    :options="allOptions"
    label="label"
    :clearable="false"
    :placeholder="placeHolder"
    :value="selectedValue"
    @input="selectHandle"    
  />
</template>

<script>

export default {
  data: () => ({
    selectedValue: null,
  }),

  props: {
    currentValue: [Number, String, Array],
    placeHolder: String,
    allOptions: Array,
  },

  mounted () {
    console.log(1111126, this.currentValue, this.placeHolder, this.allOptions);
    this.selectedValue = this.currentValue;
  },

  methods: {
    selectHandle(e) {
      console.log("selectHandle", typeof e, e.label, e.value);
      this.selectedValue = e;
      this.$emit('onSelect')
    },
  },
};

</script>
