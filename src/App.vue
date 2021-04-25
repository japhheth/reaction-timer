<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results :results="score" v-if="showResult"/>
</template>

<script>
import Results from './components/Results'
import Block from './components/Block'
export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  emits: ['closeModal'],
  data() {
    return {
      text: 'Japheth',
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  methods:{
    start(){
      this.delay = 20 * Math.random() * 500
      this.isPlaying = true
    },
    endGame(game){
      this.score = game
      this.isPlaying = false
      this.showResult = true

    }
  }
  
}
</script>

<style>
body{
  margin: 0;
  padding: 0;
}
button{
  background: #0faf87;
  color: #fff;
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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
