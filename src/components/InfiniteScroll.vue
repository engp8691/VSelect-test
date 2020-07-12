<template>
  <v-select
    :options="paginated"
    :filterable="false"
    :clearable="false"
    :value="currentValue"
    :placeholder="placeHolder"
    @input="selectHandle" 
    @open="onOpen"
    @close="onClose"
    @search="query => search = query"
  >
    <template #list-footer v-if="hasNextPage">
      <li ref="load" class="loader">
        Loading more options...
      </li>
    </template>
  </v-select>
</template>

<script>
import Vue from 'vue'
import vSelect from 'vue-select'

import 'vue-select/dist/vue-select.css';

Vue.component('v-select', vSelect)

export default {
  name: "InfiniteScroll",
  data: () => ({
    observer: null,
    limit: 21,
    search: '',
    currentValue: null,
  }),
  mounted () {
    console.log(11111, this.selectedValue, this.placeHolder);
    this.currentValue = this.selectedValue;
    this.observer = new IntersectionObserver(this.infiniteScroll);
  },
  props: {
    selectedValue: [Number, String, Array],
    allOptions: Array,
    placeHolder: String,
  },
  computed: {
    filtered () {
      return this.allOptions.filter(option => option.includes(this.search));
    },
    paginated () {
      return this.filtered.slice(0, this.limit);
    },
    hasNextPage () {
      return this.paginated.length < this.filtered.length;
    },
  },
  methods: {
    selectHandle(e) {
      console.log("selectHandle", e);
      this.currentValue = e;
      this.$emit('onSelect')
    },
    async onOpen () {
      if (this.hasNextPage) {
        await this.$nextTick();
        this.observer.observe(this.$refs.load)
      }
    },
    onClose () {
      this.observer.disconnect();
    },
    async infiniteScroll ([{isIntersecting, target}]) {
      if (isIntersecting) {
        const ul = target.offsetParent;
        const scrollTop = target.offsetParent.scrollTop;
        this.limit += 21;
        await this.$nextTick();
        ul.scrollTop = scrollTop;
      }
    }
  }
}
</script>

<style scoped>
  .loader {
    text-align: center;
    color: #bbbbbb;
  }
</style>
