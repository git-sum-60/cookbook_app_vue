<template>
  <div class="recipes-show">
    <h1>title: {{ recipe.title }}</h1>
    <h1>ingredients: {{ recipe.ingredients }}</h1>
    <h1>directions: {{ recipe.directions }}</h1>
    <h1>prep_time: {{ recipe.prep_time }}</h1>
    <a v-bind:href="`/recipes/${recipe.id}/edit`">Edit this Recipe</a>
    <h1>image_url: {{ recipe.image_url }}</h1>
    <img v-bind:src="recipe.image_url">
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      message: "Welcome to the show!",
      recipe: {}
    };
  },
  created: function() {
    // console.log(this.$route.params.id)
    axios.get('/api/recipes/' + this.$route.params.id).then(response => {
      console.log(response.data);
      this.recipe = response.data;
    })
  },
  methods: {}
};
</script>
