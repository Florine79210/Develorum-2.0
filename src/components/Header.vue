<template>
  <nav class="navbar navbar-expand-lg navbar-dark fixed-top">
    <router-link to="/">
      <h2 class="navbar-brand me-auto ms-5 text-info siteName">Develorum</h2>
    </router-link>
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
    
      <NavBar />
  
  </nav>
</template>

<script>
import NavBar from "./NavBar.vue";

export default {
  name: "Header",
  components: {
    NavBar,
  },
};
</script>

<style>
nav {
  background-color: #08065f;
  color: white;
 
}
.siteName {
  font-family: "Press Start 2P", cursive;
  font-size: 40px;
  /* text-decoration: none; */
}
.navbar ul li p {
  font-size: 20px;
  text-decoration: none;
}
</style>