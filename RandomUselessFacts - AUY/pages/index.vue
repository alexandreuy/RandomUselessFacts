<template>
  <div class="container">
    <div>
      <h1 class="title" v-on:click="update">
        {{ sentence }}
      </h1>
      <h2 class="subtitle">
        A useless fact per day
      </h2>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      sentence: 'Default'
    }
  },
  methods: {
    update(){
      axios.get('https://uselessfacts.jsph.pl/random.json?language=en').then(response => this.sentence = response.data.text)
    }
  },
  mounted(){
    axios.get('https://uselessfacts.jsph.pl/random.json?language=en').then(response => this.sentence = response.data.text)
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
