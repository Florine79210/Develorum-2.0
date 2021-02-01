<template>
  <nav class="navbar navbar-expand-lg navbar-dark fixed-top">
    <router-link to="/">
      <h2 class="navbar-brand me-auto ms-5 text-info siteName">Develorum</h2>
    </router-link>
    <button
      class="navbar-toggler me-5 ms-auto text-white"
      type="button"
      data-bs-toggle="collapse"
      data-bs-target="#navbarNav"
      aria-controls="navbarNav"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon text-white"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarNav">
      <NavBar />
    </div>
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
</style>