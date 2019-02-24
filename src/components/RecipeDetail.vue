<template lang="html">
  <div v-if='recipe'>
    <h2>{{recipe.title}}</h2>
    <img :src="recipe.thumbnail" :alt="recipe.title" height="150">
    <h3>Ingredients: {{recipe.ingredients}}</h3>
<p>Recipe {{ recipe.href }}</p>







    </div>
</template>

<script>
export default {
  name: 'recipe-detail',
  props: ['recipe']
}
</script>

<style lang="css" scoped>

</style>
