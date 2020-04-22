<template>
  <div class="recipes-show">
    <h1>title: {{ recipe.title }}</h1>
    <h1>ingredients: {{ recipe.ingredients }}</h1>
    <h1>directions: {{ recipe.directions }}</h1>
    <h1>prep_time: {{ recipe.prep_time }}</h1>

    
    
    <a v-if="recipe.user_id === $parent.getUserId()" v-bind:href="`/recipes/${recipe.id}/edit`">Edit this Recipe</a>
    
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
      // console.log('recipe user id')
      // console.log(typeof this.recipe.user_id)
      // console.log('current_user id')
      // console.log(typeof this.$parent.getUserId());
    })
  },
  methods: {

  }
};
</script>
