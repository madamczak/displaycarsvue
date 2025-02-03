<template>
  <div id="app">
    <CarsTable/>
     <!-- <DatesSelect /> -->
  </div>
</template>

<script>
import CarsTable from './components/CarsTable.vue'
// import DatesSelect from './components/dateselect.vue'

export default {
  name: 'App',
  components: {
    // DatesSelect
    CarsTable
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
