<template>
  <div id="app">
    <KaasList />
  </div>
</template>

<script>
import KaasList from './components/KaasList.vue'

export default {
  name: 'App',
  components: {
    KaasList
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
