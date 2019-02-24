<template lang="html">
<li v-on:click="handleClick">{{recipe.results}}</li>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'list-item',
  props: ['recipe'],
  methods: {
    handleClick(){
      console.log('recipe', this.recipe);
    }
  }
}
</script>


<style lang="css" scoped>
</style>
