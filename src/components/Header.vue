<template>
  <nav class="navbar navbar-expand-lg navbar-dark fixed-top">
    <a class="navbar-brand me-auto ms-5 text-info siteName" href="#">Develorum</a>
    <button
      class="navbar-toggler"
      type="button"
      data-toggle="collapse"
      data-target="#navbarNav"
      aria-controls="navbarNav"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav me-5 ms-auto">
        <li class="nav-item">
          <a class="nav-link text-white" href="#">Example 1</a>
        </li>
        <li class="nav-item">
          <a class="nav-link text-white" href="#">Example 2</a>
        </li>
        <li class="nav-item">
          <a class="nav-link text-white" href="#">Example 3</a>
        </li>
      </ul>
    </div>
    <NavBar />
  </nav>
  
</template>

<script>
import NavBar from "./NavBar.vue";

export default {
  name: "Header",
  components: {
    NavBar
  }
};
</script>

<style>
nav {
  background-color:#08065f;
  color: white;
}
.siteName {
  font-family: 'Press Start 2P', cursive;
  font-size: 40px;
}
.navbar ul {
  list-style: none;
}
.navbar ul li a {
  font-size: 20px;
  text-decoration: none;
}
</style>