<template>
  <div id="app">
    <!-- Wrapper -->
<div id="wrapper">

  <!-- Main -->
    <div id="main">
      <div class="inner">

        <!-- Header -->
          <header id="header">
            <a href="index.html" class="logo"><strong>Editorial</strong> by HTML5 UP</a>
            <ul class="icons">
              <li><a href="#" class="icon brands fa-twitter"><span class="label">Twitter</span></a></li>
              <li><a href="#" class="icon brands fa-facebook-f"><span class="label">Facebook</span></a></li>
              <li><a href="#" class="icon brands fa-snapchat-ghost"><span class="label">Snapchat</span></a></li>
              <li><a href="#" class="icon brands fa-instagram"><span class="label">Instagram</span></a></li>
              <li><a href="#" class="icon brands fa-medium-m"><span class="label">Medium</span></a></li>
            </ul>
          </header>

          <router-view />


      </div>
    </div>

  <!-- Sidebar -->
    <div id="sidebar">
      <div class="inner">

        <!-- Search -->
          <section id="search" class="alt">
            <form method="post" action="#">
              <input type="text" name="query" id="query" placeholder="Search" />
            </form>
          </section>

        <!-- Menu -->
          <nav id="menu">
            <header class="major">
              <h2>Menu</h2>
            </header>
            <ul>
              <li><a href="/recipes">Homepage</a></li>
              <li><a href="/recipes/new">Make a new Recipe</a></li>
              <li><a href="/login">Login</a></li>
              <li>
                <span class="opener">Submenu</span>
                <ul>
                  <li><a href="#">Lorem Dolor</a></li>
                  <li><a href="#">Ipsum Adipiscing</a></li>
                  <li><a href="#">Tempus Magna</a></li>
                  <li><a href="#">Feugiat Veroeros</a></li>
                </ul>
              </li>
              <li><a href="#">Etiam Dolore</a></li>
              <li><a href="#">Adipiscing</a></li>
              <li>
                <span class="opener">Another Submenu</span>
                <ul>
                  <li><a href="#">Lorem Dolor</a></li>
                  <li><a href="#">Ipsum Adipiscing</a></li>
                  <li><a href="#">Tempus Magna</a></li>
                  <li><a href="#">Feugiat Veroeros</a></li>
                </ul>
              </li>
              <li><a href="#">Maximus Erat</a></li>
              <li><a href="#">Sapien Mauris</a></li>
              <li><a href="#">Amet Lacinia</a></li>
            </ul>
          </nav>

        <!-- Section -->
          <section>
            <header class="major">
              <h2>Ante interdum</h2>
            </header>
            <div class="mini-posts">
              <article>
                <a href="#" class="image"><img src="images/pic07.jpg" alt="" /></a>
                <p>Aenean ornare velit lacus, ac varius enim lorem ullamcorper dolore aliquam.</p>
              </article>
              <article>
                <a href="#" class="image"><img src="images/pic08.jpg" alt="" /></a>
                <p>Aenean ornare velit lacus, ac varius enim lorem ullamcorper dolore aliquam.</p>
              </article>
              <article>
                <a href="#" class="image"><img src="images/pic09.jpg" alt="" /></a>
                <p>Aenean ornare velit lacus, ac varius enim lorem ullamcorper dolore aliquam.</p>
              </article>
            </div>
            <ul class="actions">
              <li><a href="#" class="button">More</a></li>
            </ul>
          </section>

        <!-- Section -->
          <section>
            <header class="major">
              <h2>Get in touch</h2>
            </header>
            <p>Sed varius enim lorem ullamcorper dolore aliquam aenean ornare velit lacus, ac varius enim lorem ullamcorper dolore. Proin sed aliquam facilisis ante interdum. Sed nulla amet lorem feugiat tempus aliquam.</p>
            <ul class="contact">
              <li class="icon solid fa-envelope"><a href="#">information@untitled.tld</a></li>
              <li class="icon solid fa-phone">(000) 000-0000</li>
              <li class="icon solid fa-home">1234 Somewhere Road #8254<br />
              Nashville, TN 00000-0000</li>
            </ul>
          </section>

        <!-- Footer -->
          <footer id="footer">
            <p class="copyright">&copy; Untitled. All rights reserved. Demo Images: <a href="https://unsplash.com">Unsplash</a>. Design: <a href="https://html5up.net">HTML5 UP</a>.</p>
          </footer>

      </div>
    </div>

</div>
  </div>
</template>

<style>
 
</style>


<script>
export default {
  data: function() {
    return {
      titleFilter: ""
    }
  },
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