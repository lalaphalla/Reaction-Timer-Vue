<template>
  <h1>MY REACTION TIMER</h1>  
  <br>
  <button class="btn" @click="start" :disabled="isPlaying">PLAY</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Result v-if="showResult" :score="score" :title="title"/>
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  data(){
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
      title: "You have fail me"
    }
  }
  ,
  components: {
    Block,
    Result
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResult = false
  },
  endGame(reactionTime){
    this.score = reactionTime
    this.isPlaying = false
    this.showResult = true
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
body{
  background: rgb(238, 214, 214);
}
h1{
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
.btn {
  position: relative;

  display: block;
  margin: 10px auto;
  padding: 10px 20px;

  overflow: hidden;

  border-width: 0;
  outline: none;
  border-radius: 2px;
  box-shadow: 0 1px 4px rgba(0, 0, 0, .6);
  
  background-color: #2ecc71;
  color: #ecf0f1;
  cursor: pointer;
  transition: background-color .3s;
}
.btn[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}

</style>
