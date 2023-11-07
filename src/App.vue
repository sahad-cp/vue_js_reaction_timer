<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default{
  components:{ Block,Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score:0,
      showResult: false
    };
  },
  methods:{
    start(){
     this.delay = 2000 + Math.random()* 5000
     this.isPlaying = true;
     this.showResult = false;
   },
   endGame(reactionTime){
    this.score = reactionTime
    this.isPlaying = false;
    this.showResult = true;
   }

  },
  
}

</script>

<template>
  <h1>Welcome</h1>
  <button @click="start" :disabled="isPlaying">Play</button>  
  <Block v-if="isPlaying" :delay="delay" @end="endGame "/>
  <Results v-if="showResult " :score="score"/>
</template>

<style scoped>
button{
  margin: 0px auto;
}
p{
  color: black;
}
</style>
