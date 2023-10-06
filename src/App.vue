//TEMPLATE
<template>
  <div class='app'>
    <h1>Reaction Timer 🏎</h1>
    <button @click="start" :disabled="isPlaying" class='my-button'>play</button>
    <!-- <p>{{ isPlaying }}</p>
    <p>{{ delay }}</p> -->
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Results :score="score" />
    <button v-if="score" @click="restart" class='my-button'>restart</button>

    <div v-if="highScore" class='high-score'>Highscore <strong>{{ highScore }}</strong> ms</div>
  </div>
</template>


//SCRIPT
<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
export default {
  name: 'App',
  components: {
    Block, Results
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      highScore: 0,
    }
  },
  methods: {
    start () {
      this.delay = 2000 + Math.random() * 2000
      this.isPlaying = true
    },
    restart () {
      this.delay = 0
      this.isPlaying = false
      this.score = null
    },
    endGame (time) {
      this.score = time
      if(this.highScore === 0 || time < this.highScore) this.highScore = time
    }
  }
}
</script>


//STYLE
<style>
#app {
  
}

.app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 10px;
}
.app h1 {
  color: #00b380;
  margin: 0 auto;
}

.high-score {
  position: fixed;
  bottom: 10px;
  margin: 0 auto;
}
</style>