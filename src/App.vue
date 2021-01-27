<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <ExampleTimeline :data=jsonData />
  </div>
</template>

<script>
import ExampleTimeline from './components/ExampleTimeline.vue';
// TOOD some try catch JSON validation? Depends how we will get the data and how reliable they are.
import jsonData from './data/timeline.json';

export default {
  name: 'App',
  data() {
    return {
      jsonData
    };
  },
  components: {
    ExampleTimeline,
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

  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
  /* TODO prettier font */
}
</style>
