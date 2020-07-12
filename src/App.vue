<template>
  <div id="app">
    <WithVueSelect  :allOptions="years" :currentValue="savedYear" placeHolder="Year" />
    <WithVueSelect  :allOptions="months" :currentValue="savedMonth" placeHolder="Month" />
    <WithVueSelect  :allOptions="days" :currentValue="savedDay" placeHolder="Day" />
    <WithVueSelect  :allOptions="allCountries" :currentValue="savedCountry" placeHolder="Country" />
  </div>
</template>

<script>
import WithVueSelect from './components/WithVueSelect.vue';
import countryCodes from "./components/data/countryCodes";

export default {
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
  name: 'App',
  components: {
    WithVueSelect,
  }
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
