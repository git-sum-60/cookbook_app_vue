<template>
  <div id="app">
    <div id="nav">      
      <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <a class="navbar-brand" href="/">Home</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav mr-auto">
            <li class="nav-item active">
              <a class="nav-link" href="/recipes">Recipes index <span class="sr-only">(current)</span></a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="/recipes/new">New Recipe</a>
            </li>
            <li class="nav-item dropdown">
              <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                Auth
              </a>
              <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                <a v-if="!isLoggedIn()" class="dropdown-item" href="/login">Login</a>
                <a v-if="isLoggedIn()" class="dropdown-item" href="/logout">Logout</a>
                <div class="dropdown-divider"></div>
                <a v-if="!isLoggedIn()" class="dropdown-item" href="/signup">Signup</a>
              </div>
            </li>
            <li class="nav-item">
              <a class="nav-link disabled" href="#">Disabled</a>
            </li>
          </ul>
          <form class="form-inline my-2 my-lg-0">
            <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
            <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
          </form>
        </div>
      </nav>      
    </div>
    <p v-if="isLoggedIn()">I am Logged in</p>
    <p v-else-if="!isLoggedIn()">I am NOT Logged in</p>
    <router-view/>
  </div>
</template>

<style>
  #app {
    font-family: Futura,"Trebuchet MS",Arial,sans-serif;
  }

  body {
    background-image: url('./assets/purty_wood.png')
  }
</style>


<script>
export default {
  methods: {
    isLoggedIn: function() {
      console.log(' i am checking if i\'m logged in')
      if (localStorage.getItem("jwt")) {
        return true
      } else {
        return false
      }
    },
    getUserId: function() {
       return parseInt(localStorage.getItem("user_id"));
    }
  }
}
</script>