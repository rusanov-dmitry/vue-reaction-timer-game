<template>
  <h1>Reaction Timer</h1>
  <button @click="startGame" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score">
    <p>Your score is: <span>{{ score }} ms</span></p>
  </Results>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    startGame() {
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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button {
  padding: 15px 35px;
  border: none;
  border-radius: 5px;
  font-size: 16px;
  font-weight: 600;
  background: rgb(120, 83, 207);
  color: white;
  cursor: pointer;
}
button:disabled {
  background: rgb(187, 168, 231);
}
</style>
