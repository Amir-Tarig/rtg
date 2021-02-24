<template>
  <h1>Reaction Timer Game</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <block :delay="delay" v-if="isPlaying" @end="endGame"/>
  <results v-if="showResults" :score="score"></results>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.floor(Math.random() * 5000)
      this.isPlaying = true
      this.showResults = false 
    },
    endGame(reactionTimer) {
      this.score = reactionTimer
      this.isPlaying = false
      this.showResults = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
