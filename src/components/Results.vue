<template>
  <div class="results">
    <br><br>
    <OneResult v-for="res in resultsList" :key="res.key" :url="res.url" :title="res.title" :desc="res.description"/>
  </div>
</template>

<script>
import OneResult from './OneResult.vue'
export default {
  name: 'Results',
  props: {
    resultsList: Array
  },
  components: {
      OneResult
  },
  data() {
    return {
    }
  },
  methods: {
    countResults() {
        return this.resultsList.length;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.results {
    width: 60%;
    margin: 0 auto;
}
</style>
