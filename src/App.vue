<template>
  <div id="app">
    <h1>MAIN APP</h1>
    <DataLoader />
    <DataViz />
  </div>
</template>

<script>
import DataLoader from './components/DataLoader.vue';
import DataViz from './components/DataViz.vue';

export default {
  name: 'App',
  components: {
    DataLoader,
    DataViz
  }
}
</script>

<style>
body {
  color: white;
  background: black;
}

h1 {
  text-align: center;
}
</style>
