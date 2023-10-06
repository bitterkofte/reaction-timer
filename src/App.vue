//TEMPLATE
<template>
  <div class='app'>
    <h1>Reaction Timer 🏎</h1>
    <button @click="start" :disabled="isPlaying" class='my-button'>play</button>
    <!-- <p>{{ isPlaying }}</p>
    <p>{{ delay }}</p> -->
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <p v-if="score">Reaction Time: <strong>{{ score }}</strong> ms</p>
    <button v-if="score" @click="restart" class='my-button'>restart</button>
  </div>
</template>


//SCRIPT
<script>
import Block from './components/Block.vue'
export default {
  name: 'App',
  components: {
    Block
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
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

</style>