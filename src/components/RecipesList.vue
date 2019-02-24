<template lang="html">
  <div>
    <ul>
      <list-item v-for="(recipe, index) in recipes.results" :recipe="recipe" :key="index"></list-item>
    </ul>
  </div>

</template>

<script>
import ListItem from './ListComponent.vue';

export default {
  name: 'recipe-list',
  props: ['recipes'],
  components: {
    "list-item": ListItem
  }
}
</script>

<style lang="css" scoped>
</style>
