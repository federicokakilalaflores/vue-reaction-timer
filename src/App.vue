<template>
  <h1>VUE REACTION TIMER</h1>
  <button class="play-button" @click="start" :disabled="isPlaying">Play Game</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Result v-if="score" :score="score"/>
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: {
    Block,
    Result
  },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null
    }
  },
  methods: {
    start(){
      this.delay = (Math.random() * (6000 - 2000)) + 2000 
      this.isPlaying = true
      this.score = null;
    },
    endGame(reactionTime){
      this.score = reactionTime;
      this.isPlaying = false;
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
  color: #2c3e50;
  margin-top: 60px;
}

.play-button{
  padding: 12px 15px;
  border: 0;
  color: white;
  background-color: teal;
  border-radius: 4px;
}

.play-button:hover{
  cursor: pointer;
}

.play-button:disabled{
  opacity: 0.2;
  background: #888;
  color: lightgrey;
  cursor: not-allowed;
}
</style>
