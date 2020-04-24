<template>
  <div class="recipes-index">
    <h1>{{ message }}</h1>
    Find your recipe here: <input type="text" v-model="titleFilter" list="titles">

    <datalist id="titles">
      <option v-for="recipe in recipes">{{recipe.title}}</option>
    </datalist>
    
    <button v-on:click="setSortAttribute('prep_time')">Sort by prep_time</button>
    <button v-on:click="setSortAttribute('title')">Sort by title</button>
    <button v-on:click="setSortAttribute('ingredients')">Sort by ingredients</button>

    <transition-group appear enter-active-class="animated jello" leave-active-class="animated rubberBand">
      <div 
        v-for="recipe in orderBy(filterBy(recipes, titleFilter, 'title'), sortAttribute, 1)" 
        v-on:click="currentRecipe = recipe" 
        v-bind:class="{selected: currentRecipe === recipe}"
        v-bind:key="recipe.id"
      >
        <p>title: <a v-bind:href="`/recipes/${recipe.id}`">{{ recipe.title }}</a></p>
        <p>ingredients: {{ recipe.ingredients }}</p>
        <p>directions: {{ recipe.directions }}</p>
        <p>prep_time: {{ recipe.prep_time }}</p>
        <p>image_url: {{ recipe.image_url }}</p>
        <hr>
      </div>
    </transition-group>
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
      titleFilter: '',
      sortAttribute: "directions"
    };
  },
  created: function() {
    axios.get('/api/recipes').then(response => {
      console.log(response.data)
      this.recipes = response.data
    })
  },
  methods: {
    setSortAttribute: function(attribute) {
      console.log(attribute);
      console.log('setting sort attribute...')
      this.sortAttribute = attribute;
    }
  }
};
</script>
