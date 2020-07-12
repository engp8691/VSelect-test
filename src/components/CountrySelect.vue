<template>
  <v-select
    placeholder="Choose a country"
    label="label"
    :value="currentValue"
    :options="countryCodes"
  />
</template>
<script>
import countryCodes from "./data/countryCodes";
export default {
  data: () => ({
    currentValue: { value: "DZ", label: "Algeria" }
  }),
  computed: {
    countryCodes: () => countryCodes
  }
};
</script>