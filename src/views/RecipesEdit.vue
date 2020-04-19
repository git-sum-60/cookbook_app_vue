<template>
  <div class="recipes-new">
    <div class="container">      
      <form v-on:submit.prevent="submit()">
        <h1>Edit a Recipe</h1>
        <ul>
          <li class="text-danger" v-for="error in errors">{{ error }}</li>
        </ul>
        <div class="form-group">
          <label>Title:</label> 
          <input type="text" class="form-control" v-model="recipe.title">
        </div>
        <div class="form-group">
          <label>Directions:</label>
          <input type="text" class="form-control" v-model="recipe.directions">
        </div>
        <div class="form-group">
          <label>Ingredients:</label>
          <input type="text" class="form-control" v-model="recipe.ingredients">
        </div>
        <div class="form-group">
          <label>Prep Time:</label>
          <input type="text" class="form-control" v-model="recipe.prep_time">
        </div>

        <!-- <textarea rows="30" cols="80"></textarea> -->

        <div class="form-group">
          <label>Image Url:</label>
          <input type="text" class="form-control" v-model="recipe.image_url">
        </div>
        <input type="submit" class="btn btn-primary" value="Submit">
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      recipe: {},
      errors: [],      
    };
  },
  created: function() {
    console.log('in created on edit page')
    axios.get(`/api/recipes/${this.$route.params.id}`).then(response => {
      console.log(response.data);
      this.recipe = response.data;
    })
  },
  methods: {
    submit: function() {
      
      
      var params = {
        title: this.recipe.title,
        ingredients: this.recipe.ingredients,
        directions: this.recipe.directions,
        prep_time: this.recipe.prepTime,
        image_url: this.recipe.imageUrl
      };

      console.log('params')
      console.log(params);
      axios
        .patch(`/api/recipes/${this.recipe.id}`, params)
        .then(response => {
          this.$router.push("/recipes");
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    }
  }
};


// show the form
// prepopulate data in form
// send data to rails



</script>


