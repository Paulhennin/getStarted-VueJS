<template>
  <div id="root">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <ContentPage />
  </div>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import ContentPage from './components/ContentPage.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    ContentPage
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
