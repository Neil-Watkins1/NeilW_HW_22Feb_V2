<template>
  <div>
    <h1>Recipes</h1>
    <div class="main-container">
      <recipes-list :recipes='recipes'></recipes-list>

    </div>
  </div>
</template>

<script>
import RecipesList from './components/RecipesList.vue';

import {eventBus} from './main.js'

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
    .then(recipes => this.recipes = recipes)


  },
  components: {
    "recipes-list": RecipesList

  }
}
</script>

<style>
  .main-container {
    display: flex;
    justify-content: space-between;
  }
</style>
