<template>
  <div id="app">
    <WithVueSelect      
      :options="years"
      :currentValue="savedYear"
      placeHolder="Year"
      @onSelect="onSelect"
    />

    <WithVueSelect      
      :options="months"
      :currentValue="savedMonth"
      placeHolder="Month"
      @onSelect="onSelect"
    />

    <WithVueSelect      
      :options="days"
      :currentValue="savedDay"
      placeHolder="Day"
      @onSelect="onSelect"
    />

    <WithVueSelect       
      :options="allCountries"
      :currentValue="savedCountry"
      placeHolder="Country"
      @onSelect="onSelect" 
    />
  </div>
</template>

<script>
import WithVueSelect from './components/WithVueSelect.vue';
import countryCodes from "./components/data/countryCodes";

export default {
  name: 'App',
  components: {
    WithVueSelect,
  },
  data: () => ({
    args: null,
  }),
  computed: {
    years(){
      const years = [];
      for(let i=2020; i>1900; i--){
        years.push(`${i}`);
      }      
      return years;
    },
    months(){
      return [
        "January",
        "Febuary",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "Octable",
        "November",
        "December",
      ];
    },
    days(){
      const days = [];
      for(let i=1; i<32; i++){
        days.push(`${i}`);
      }      
      return days;
    },
    allCountries(){
      return countryCodes;
    },
    savedYear(){
      return 1966;
    },
    savedMonth(){
      return "December";
    },
    savedDay(){
      return 6;
    },
    savedCountry(){
      return {value: "AG", label: "Antigua and Barbuda"};
    }
  },
  methods: {
    onSelect: function (value) {
      console.log(value)
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
