<template>
  <div>
    <h1>Recipes</h1>
    <div class="main-container">
      <recipes-list :recipes='recipes'></recipes-list>
      <recipe-detail :recipe='selectedRecipe'></recipe-detail>
    </div>
  </div>
</template>



<script>
import { eventBus } from './main.js';
import RecipesList from './components/RecipesList.vue';
import RecipeDetail from './components/RecipeDetail.vue';

export default {
  name: 'app',
  data(){
    return {
      recipes: [],
      selectedRecipe: null
    };
  },
  mounted(){
    fetch('http://www.recipepuppy.com/api/')
    .then(res => res.json())
    .then(recipes => this.recipes = recipes.results)

       eventBus.$on('recipe-selected', (recipe) => {
         this.selectedRecipe = recipe
       })

},
  components: {
    "recipes-list": RecipesList,
    "recipe-detail": RecipeDetail

  }
}
</script>

<style>
  .main-container {
    display: flex;
    justify-content: space-between;
  }
</style>
