<template>
<h1>Ninja Reaction Timer</h1>
<button v-on:click="startGame" v-bind:disabled="isPlaying">Play</button>
<Block v-if="isPlaying" v-bind:delayAmount="delay" @end="endGame" />
<Results v-if="showResults" v-bind:playerScore="score" />
</template>

<script>
import Block from './components/Block'
import Results from './components/Results'

export default {
  name: 'App',
  data(){
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  components: {
    Block,
    Results
  },
  methods:{
    startGame(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
      console.log(this.delay)
    },
    endGame(reactionTime){
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
    background: #0faf87;
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 4px;
    font-size: 16px;
    letter-spacing: 1px;
    cursor: pointer;
    margin: 10px;
  }
  button[disabled] {
    opacity: 0.2;
    cursor: not-allowed;
  }
</style>
