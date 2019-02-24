<template>
  <div>
    <h1>What's For Dinner?</h1>
    <h2>Why Not Try:</h2>
    <div class="main-container">
      <recipes-list :recipes='recipes'></recipes-list>
      <div id="recipedetail">
        <recipe-detail :recipe='selectedRecipe'></recipe-detail>
        </div>
    </div class='ingredient-search'>
    <form action="">
  Favourite Ingredient:<br>
  <input type="text" name="Ingredient" value="Ingredient">
<input type="submit" value="New Recipes Please">
</form>
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
    border: 10px 10px 10px 80px;
    padding:10px 10px 10px 80px;
    justify-content: space-between;
    font-family: 'Lora', serif;

  }

.ingredient-input {

  border: 10px 10px 10px 80px;
  padding:10px 10px 10px 80px;
  justify-content: space-between;

}
h1, h2 {
  text-align: inherit;
  border: 10px 10px 10px 80px;
  padding:10px 10px 10px 50px;
}



  html{

    font-family: 'Lora', serif;
    background-color: rgb(230, 255, 255);


}
</style>
