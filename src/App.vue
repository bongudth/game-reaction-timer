<template>
  <h1>Ninja Reaction Timer</h1>
  <button class="button" @click="startGame" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delayTime="delayTime" @end="endGame" />
  <Results v-if="score" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block,
    Results,
  },
  data() {
    return {
      isPlaying: false,
      delayTime: null,
      score: null,
      showResults: false,
    }
  },
  methods: {
    startGame() {
      this.score = null;
      this.isPlaying = true;
      this.delayTime = 1000 + Math.random() * 2000;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
    }
  },
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
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 20px;
  }
  .button {
    background-color: rgb(34, 187, 93);
    color: aliceblue;
    padding: 10px 20px;
    border: none;
    border-radius: 10px;
  }
  .button:disabled {
    cursor: not-allowed;
    opacity: 0.5;
  }
</style>
