<template>
  <div>
    <h1>Reaction Timer</h1>
    <button class="start-button" @click="start" :disabled="isPlaying"> START </button>
    <Block v-if="isPlaying" :delay="delay" @end='endGame' />
    <Results v-if="showResults" :score="score" />
  </div>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
  }
}
</script>

<style>
h1 {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.start-button {
    width: 100px;
    padding: 10px 5px;
    font-weight: bold;
    border: none;
    background: #b7c1f8;
    margin: 0 auto;
    position: relative;
    left: 50%;
    transform: translateX(-50%);
}
.start-button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
