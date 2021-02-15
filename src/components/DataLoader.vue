<template>
  <div>
    <button @click="getData">Get Data</button>
  </div>
</template>

<script>
import { eventBus } from '../main';

export default {
  name: 'DataLoader',
  methods: {
    getData() {
      fetch('https://jsonplaceholder.typicode.com/posts')
        .then(resp => resp.json())
        .then(data => {
          // console.log(data);
          eventBus.$emit('data', data);
        })
    }
  }
}
</script>

<style scoped>

</style>
