//TEMPLATE
<template>
<div class='results'>
  <p v-if="score">Reaction Time: <strong>{{ score }}</strong> ms</p>
</div>
</template>


//SCRIPT
<script>
export default {
  props: ['score'],
  data() {
    return {
      
    }
  },
  methods: {
    
  },
}
</script>


//STYLE
<style>
.results {
  
}
</style>