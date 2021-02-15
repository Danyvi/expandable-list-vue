<template>
  <div>
    <div class="dataVizContainer">
      <ul>

        <li 
          v-for="post in data" 
          :key="post.id"
        >
          <a @click="displayRef('p-' + post.id)">{{ post.title }}</a>

					<p
						style="display:none"
            :ref="'p-' + post.id"
            @click="hideBody('p-' + post.id)" 
          >
            <a>{{ post.body }}</a>
          </p>

        </li>

      </ul>
    </div>
  </div>

</template>

<script>
import { eventBus } from '../main';

export default {
  data() {
    return {
      data: [],
      isVisible: false,
    }
  },
  methods: {
    displayRef(ref) {
      console.log(this.$refs[ref][0]) // <= accessing the dynamic ref
      this.$refs[ref][0].style.display = 'block';
    },
    hideBody(ref) {
			console.log(this.$refs[ref][0]) 
      this.$refs[ref][0].style.display = 'none';
    }
  },
  mounted() {
    eventBus.$on('data', receivedData => {
      console.log('Data received: ', receivedData);
      this.data = receivedData;
    })
  }
}
</script>

<style scoped>

ul {
  margin: 0 auto;
  width: 40%;
  list-style: none;
}

li {
  margin: 0.5rem 0;
}
li:nth-child(odd) {
  color: yellow;
}
li:nth-child(even) {
  color: aqua;
}
a {
  cursor: pointer;
}

</style>