<script setup>
import Block from './components/Block.vue'
</script>

<template>
  <div class="col-12 text-center">
    <h3 style="margin-top: 8.5rem;" class="text-white">Welcome to <span class="text-success">Reaction</span> timer game :)</h3>
    <button :disabled="isPlaying" class="mt-4 mb-4 btn btn-outline-success play-btn m-2" @click="start">Play!</button>
    <button v-if="isPlaying == true" class="mt-4 mb-4 btn btn-outline-danger play-btn m-2" @click="reset">Restart!</button>
    <br>
    <small class="text-white">click the box fast asap</small>
    <p v-if="score" class="mt-4 text-white">Reaction result : {{ score }} ms</p>
  </div>
  <Block v-if="isPlaying" :delay="delay" :boxTip="boxTip" @end="endGame" />
</template>

<script>
export default{
  data(){
    return {
      isPlaying:false,
      delay:null,
      score:null,
    }
  },
  methods:{
    start(){
      this.isPlaying = true
      this.delay = ((Math.random() * 4) + 1 )*1000 // sec to ms
    },
    reset(){
      this.isPlaying = false
      this.score = null
    },
    endGame(score){
      this.score = score
    }
  }
}
</script>

<style>
.play-btn{
  transition: .2s;
  height: 50px;
  width: 150px;
}
</style>

