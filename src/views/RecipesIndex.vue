<template>
  <div class="recipes-index">
    <h1>{{ message }}</h1>
    <div v-for="recipe in recipes" v-on:click="currentRecipe = recipe" v-bind:class="{selected: currentRecipe === recipe}">
      <p>title: <a v-bind:href="`/recipes/${recipe.id}`">{{ recipe.title }}</a></p>
      <p>ingredients: {{ recipe.ingredients }}</p>
      <p>directions: {{ recipe.directions }}</p>
      <p>prep_time: {{ recipe.prep_time }}</p>
      <p>image_url: {{ recipe.image_url }}</p>
      <hr>
    </div>
  </div>
</template>

<style>
  .selected {
    color: white;
    background-color: steelBlue;
  }
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      recipes: [],
      currentRecipe: {}
    };
  },
  created: function() {
    axios.get('/api/recipes').then(response => {
      console.log(response.data)
      this.recipes = response.data
    })
  },
  methods: {}
};
</script>
