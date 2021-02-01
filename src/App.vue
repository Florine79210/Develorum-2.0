<template>
  <div class="text-center justify-content-center pt-5 mt-2">
    <Header />
    <div class="container-fluid mt-5 m-auto">
      <div class="row d-flex justify-content-center">
        <div class="col-md-3">
          <Form />
        </div>
        <div class="col-md-6">
          <MessagesList :messages="messages" />
        </div>
        <div class="col-md-3"></div>
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Form from "./components/Form.vue";
import MessagesList from "./components/MessagesList.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    Header,
    Form,
    MessagesList,
    Footer,
  },

  data() {
    return {
      messages: null,
      error: false,
    };
  },

  created: function () {
    axios
      .get("https://cors-anywhere.herokuapp.com/https://crudcrud.com/api/c2659c124102448995b5072baf0c6409/message")

      .then((res) => {
        this.messages = res.data;
        console.log(this.messages);
      })
      .catch((error) => {
        this.error = true;
        console.log(error);
      });
  },
};
</script>

<style>
#app {
  font-family: "Vollkorn", serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
  /* margin-top: 150px; */
}
</style>
