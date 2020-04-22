<template>
  <div class="recipes-index">
    
    <!-- Banner -->
    <section id="banner">
      <div class="content">
        <header>
          <h1>Welcome to the <br />
          Recipes Index </h1>
          <p>A free and fully responsive site template</p>
        </header>
        <p>Aenean ornare velit lacus, ac varius enim ullamcorper eu. Proin aliquam facilisis ante interdum congue. Integer mollis, nisl amet convallis, porttitor magna ullamcorper, amet egestas mauris. Ut magna finibus nisi nec lacinia. Nam maximus erat id euismod egestas. Pellentesque sapien ac quam. Lorem ipsum dolor sit nullam.</p>
        <ul class="actions">
          <li><a href="#" class="button big">Learn More</a></li>
        </ul>
      </div>
      <span class="image object">
        <img src="images/pic10.jpg" alt="" />
      </span>
    </section>

  <!-- Section -->
    <section>
      <header class="major">
        <h2>Erat lacinia</h2>
      </header>
      <div class="features">
        <article>
          <span class="icon fa-gem"></span>
          <div class="content">
            <h3>Portitor ullamcorper</h3>
            <p>Aenean ornare velit lacus, ac varius enim lorem ullamcorper dolore. Proin aliquam facilisis ante interdum. Sed nulla amet lorem feugiat tempus aliquam.</p>
          </div>
        </article>
        <article>
          <span class="icon solid fa-paper-plane"></span>
          <div class="content">
            <h3>Sapien veroeros</h3>
            <p>Aenean ornare velit lacus, ac varius enim lorem ullamcorper dolore. Proin aliquam facilisis ante interdum. Sed nulla amet lorem feugiat tempus aliquam.</p>
          </div>
        </article>
        <article>
          <span class="icon solid fa-rocket"></span>
          <div class="content">
            <h3>Quam lorem ipsum</h3>
            <p>Aenean ornare velit lacus, ac varius enim lorem ullamcorper dolore. Proin aliquam facilisis ante interdum. Sed nulla amet lorem feugiat tempus aliquam.</p>
          </div>
        </article>
        <article>
          <span class="icon solid fa-signal"></span>
          <div class="content">
            <h3>Sed magna finibus</h3>
            <p>Aenean ornare velit lacus, ac varius enim lorem ullamcorper dolore. Proin aliquam facilisis ante interdum. Sed nulla amet lorem feugiat tempus aliquam.</p>
          </div>
        </article>
      </div>
    </section>

  <!-- Section -->
    <section>
      <header class="major">
        <h2>Ipsum sed dolor</h2>
      </header>
      <div class="posts">
        <article v-for="recipe in recipes">
          <a href="#" class="image"><img v-bind:src="recipe.image_url" alt="" /></a>
          <h3>{{recipe.title}}</h3>
          <p>{{recipe.directions}}.</p>
          <p>{{recipe.prep_time}}.</p>
          <ul class="actions">
            <li><a href="#" class="button">More</a></li>
          </ul>
        </article>
      </div>
    </section>
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
