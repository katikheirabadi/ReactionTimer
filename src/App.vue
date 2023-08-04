<template>
  <h1>Reaction Timer</h1>
  <button class="btn" :class="{btndisable:isplaying}" @click="Start">New Game</button>
  <block :delay="delay" v-if="isplaying" @end="EndGame"/>
  <result :time="time" v-if="showresult"/>
</template>

<script>
import block from './components/BlockComponent.vue'
import result from './components/ResultComponent.vue'

export default {
  components: {
    block,result
  },
  data(){
    return{
      isplaying: false,
      delay: null,
      time:0,
      showresult: false
    }
  },
  methods: {
    Start(){
      this.delay = 2000 + Math.random()*2000
      this.isplaying = true
      this.showresult = false
    },
    EndGame(reactionTime){
      this.isplaying = false
      this.time = reactionTime
      this.showresult = true
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
  }
</style>
