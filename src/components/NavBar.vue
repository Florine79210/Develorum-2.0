<template>
  <div id="nav">
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav me-5 ms-auto">
        <router-link to="/posts">
          <li class="nav-item">
            <a class="nav-link text-white">Posts</a>
          </li>
        </router-link>

        <span v-if="isLoggedIn">
          <li>
            <a @click="logout" class="nav-link text-white">Logout</a>
          </li>
        </span>

        <span v-else>
          <router-link to="/register">
            <li class="nav-item">
              <a class="nav-link text-white">Register</a>
            </li>
          </router-link>

          <router-link to="/login">
            <li class="nav-item">
              <a class="nav-link text-white">Login</a>
            </li>
          </router-link>
        </span>
      </ul>
    </div>

    <!-- <router-link to="/">Home</router-link> |
    <router-link to="/posts">Posts</router-link> |
    <span v-if="isLoggedIn">
      <a @click="logout">Logout</a>
    </span>
    <span v-else>
      <router-link to="/register">Register</router-link> |
      <router-link to="/login">Login</router-link>
    </span> -->
  </div>
</template>
<script>
import { mapGetters } from "vuex";

export default {
  name: "NavBar",
  computed: {
    ...mapGetters(["auth/isAuthenticated"]),
    isLoggedIn: function () {
      return this.$store.getters.isAuthenticated;
    },
  },
  methods: {
    async logout() {
      await this.$store.dispatch("LogOut");
      this.$router.push("/login");
    },
  },
};
</script>
<style>
#nav {
  padding: 30px;
}
/* #nav a {
  font-weight: bold;
  color: #2c3e50;
}
a:hover {
  cursor: pointer;
}
#nav a.router-link-exact-active {
  color: #42b983;
} */

#nav ul li a {
  font-size: 20px;
  font-weight: bold;
  text-decoration: none;
}
</style>