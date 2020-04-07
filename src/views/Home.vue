<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h1>{{ name }}</h1>
    <!-- <h1>{{ recipes }}</h1> -->
    <!-- recipes.each do |recipe| -->
    <div v-bind:key="recipe.id" v-for="recipe in recipes">
      <p>title: {{ recipe.title }}</p>
      <p>ingredients: {{ recipe.ingredients }}</p>
      <p>image url: {{ recipe.image_url }}</p>
      <img v-bind:src="recipe.image_url">
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
      recipes: []
    };
  },
  created: function() {
    console.log('in the created');

    console.log("this outside callback")
    axios.get("/api/recipes").then(response => {
      console.log("this inside callback")
      this.recipes = response.data;
    })
  },
  methods: {}
};
</script>
