<template>
  <div id="app">
    <InfiniteScroll :allOptions="countries" :selectedValue="1916" placeHolder="Year" />
    <InfiniteScroll :allOptions="months" selectedValue="July" placeHolder="Month" />
    <InfiniteScroll :allOptions="days" :selectedValue="23" placeHolder="Day" />
  </div>
</template>

<script>
import InfiniteScroll from './components/InfiniteScroll.vue';

export default {
  computed: {
    countries(){
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
    }
  },
  name: 'App',
  components: {
    InfiniteScroll
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
