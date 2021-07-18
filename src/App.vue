<template>
  <div id="app">
    <h1>Let's test your reaction time!</h1>
    <button @click="start" :disabled="play">Take the test</button>
    <br>
    <Block 
      v-if="play" 
      :delay="delay"
      @finish="stopPlay"/>

    <div class="result" v-if="showResult">
      <h2>{{score}} ms</h2>
    </div>
  </div>
</template>

<script>
import Block from "./components/Block.vue"

export default {
  name: 'App',
  data(){
    return {
      play:false,
      delay:null,
      score:null,
      showResult:false,
    }
  },
  methods:{
    start(){
      this.play=true
      this.delay=1000 + Math.random()*3000
      this.showResult=false

    },
    stopPlay(reactionTime){
      this.play=false
      this.score=reactionTime
      this.showResult=true
    }
    
  },
  components: {
    Block,
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

button{
  height:90px;
  width: 190px;
  margin-bottom: 40px;

}
</style>
