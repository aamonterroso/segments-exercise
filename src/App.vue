<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/jlogo.png">
    <SegmentForm title="Jobsity - Segment Builder"/>
  </div>
</template>

<script>
import SegmentForm from './components/SegmentForm.vue'

export default {
  name: 'App',
  components: {
    SegmentForm
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
