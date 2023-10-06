//TEMPLATE
<template>
<div v-if="showBlock" @click="stopTimer" class='block'>
  <p>{{ reactionTime }}</p>
</div>
</template>


//SCRIPT
<script>
export default {
  props: ['delay'],
  data() {
    return {
      showBlock: false,
      showRestart: false,
      timer: null,
      reactionTime: 0
    }
  },
  methods: {
    startTimer () {
      this.timer = setInterval(() => {
        this.reactionTime ++
      }, 1)
    },
    stopTimer () {
      clearInterval(this.timer)
      this.$emit('end', this.reactionTime)
    }
  },

  mounted () {
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
  updated () {
    
  }
}
</script>


//STYLE
<style>
.block {
  text-align: center;
  background: #00b380;
  padding: 50px 55px;
  user-select: none;
}
</style>