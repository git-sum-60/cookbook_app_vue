<template>
  <div class="recipes-index">
    <h1>{{ message }}</h1>
    Find your recipe here: <input type="text" v-model="titleFilter" list="titles">

    <datalist id="titles">
      <option v-for="recipe in recipes">{{recipe.title}}</option>
      
    </datalist>
    
    <div v-for="recipe in filterBy(recipes, titleFilter, 'title', 'ingredients')" v-on:click="currentRecipe = recipe" v-bind:class="{selected: currentRecipe === recipe}">
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
    transition: background-color 4s ease;
  }
</style>

<script>
import Vue2Filters from "vue2-filters"


import axios from "axios";
export default {
  mixins: [Vue2Filters.mixin],
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      recipes: [],
      currentRecipe: {},
      titleFilter: ''
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
