<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h1>{{ name }}</h1>
    <p>Title: <input type="text" v-model="newRecipeTitle"></p>
    <p>Ingredients: <input type="text" v-model="newRecipeIngredients"></p>
    <p>Directions: <input type="text" v-model="newRecipeDirections"></p>
    <p>PrepTime: <input type="text" v-model="newRecipePrepTime"></p>
    <p>ImageUrl: <input type="text" v-model="newRecipeImageUrl"></p>
    <button v-on:click="addRecipe()">Add a new recipe</button>
    <!-- <h1>{{ recipes }}</h1> -->
    <!-- recipes.each do |recipe| -->
    <div v-bind:key="recipe.id" v-for="recipe in recipes">
      <p>id: {{ recipe.id }}</p>
      <p>title: {{ recipe.title }}</p>
      <p>ingredients: {{ recipe.ingredients }}</p>
      <p>image url: {{ recipe.image_url }}</p>
      <button v-on:click="showInfo(recipe)">Show more info</button>
      <div v-if="currentRecipe === recipe">
        <p>directions: {{ recipe.directions }}</p>
        <p>prep_time: {{ recipe.prep_time }}</p>
        <img v-bind:src="recipe.image_url">

        <p>Title: <input type="text" v-model="recipe.title"></p>
        <p>directions: <input type="text" v-model="recipe.directions"></p>
        <p>ingredients: <input type="text" v-model="recipe.ingredients"></p>
        <p>prep_time: <input type="text" v-model="recipe.prep_time"></p>
        <p>image_url: <input type="text" v-model="recipe.image_url"></p>
        <p>chef: <input type="text" v-model="recipe.chef"></p>

        <button v-on:click="updateRecipe(recipe)">Update this recipe</button>
      </div>
      <hr>
    </div>
  </div>
</template>


<style>
</style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      name: "brian",
      recipes: [],
      newRecipeTitle: "",
      newRecipeIngredients: "",
      newRecipeDirections: "",
      newRecipePrepTime: "",
      newRecipeImageUrl: "",
      currentRecipe: {}
    };
  },
  created: function() {
    console.log('in the created');

    console.log("this outside callback")
    axios.get("/api/recipes").then(response => {
      console.log("this inside callback")
      console.log(response.data)
      this.recipes = response.data;
    })
  },
  methods: {
    addRecipe: function() {
      console.log(this.newRecipeTitle)
      // get some data
      var params = {
        input_title: this.newRecipeTitle,
        input_ingredients: this.newRecipeIngredients,
        input_directions: this.newRecipeDirections,
        input_prep_time: this.newRecipePrepTime,
        input_image_url: this.newRecipeImageUrl
      }

      // send it to rails
      axios.post("/api/recipes", params).then(response => {
        console.log(response.data);
        this.recipes.push(response.data)
        this.newRecipeTitle = "";
        this.newRecipeIngredients = "";
        this.newRecipeDirections = "";
        this.newRecipePrepTime = "";
        this.newRecipeImageUrl = "";
      })
    },
    showInfo: function(theRecipe) {
      console.log('showing info...')
      console.log(theRecipe)
      this.currentRecipe = theRecipe;
    },
    updateRecipe: function(theRecipe) {
      console.log('update recipe')

      console.log(theRecipe)

      var params = {        
        title: theRecipe.title,
        ingredients: theRecipe.ingredients,  
        image_url: theRecipe.image_url,  
        directions: theRecipe.directions,  
        prep_time: theRecipe.prep_time,  
        image_url: theRecipe.image_url,
        chef: theRecipe.chef
      }

      axios.patch(`/api/recipes/${theRecipe.id}`, params).then(response => {
        console.log(response.data);
        theRecipe = response.data;
      })

    }
  }
};
</script>
