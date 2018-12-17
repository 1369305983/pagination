<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <page :total="100" :currentpage="2" :pagedisplay="20"></page>
  </div>
</template>

<script>
import page from './components/page.vue'

export default {
  name: 'app',
  components: {
    page
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
