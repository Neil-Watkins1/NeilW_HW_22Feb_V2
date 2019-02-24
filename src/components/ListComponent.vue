<template lang="html">

<li v-on:click="handleClick">{{recipe.title}}</li>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'list-item',
  props: ['recipe'],
  methods: {
    handleClick(){
      eventBus.$emit('recipe-selected', this.recipe);

    }
  }
}
</script>


<style lang="css" scoped>
</style>
