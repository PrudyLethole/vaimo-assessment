<template>
  <div id="app">
    <AssessmentData/>

    
  </div>
  
</template>

<script>
import AssessmentData from './components/AssessmentData.vue'

export default {
  name: 'App',
  components: {
    AssessmentData
  }
}
</script>

<style>
#app {
  font-family: Roboto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
