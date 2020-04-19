<template>
  <div class="recipes-index">
    <h1>{{ message }}</h1>
    <div v-for="recipe in recipes">
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
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      recipes: []
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
