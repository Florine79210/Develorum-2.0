<template>
    <div id="contentMessageModif">
        <h3 class="mb-4 pt-2 pb-2">Modifier le message</h3>

        <form @submit="checkEditForm" method="put">
          <p v-if="errors.length">
              <b>Erreur(s) !</b>
              <ul>
                  <li v-for="error in errors" v-bind:key="error.id">{{ error }}</li>
              </ul>
          </p>

          <div id="modifForm" class="card">
            <div class="card-body">

              <div class="mt-3 mb-3">
                <label for="inputMessageTitle" class="col-form-label"
                  >Intitulé du message:</label
                >
                <input
                  type="text"
                  id="inputMessageTitle"
                  name="inputMessageTitle"
                  v-model="inputMessageTitle"
                  class="form-control text-center text-white"
                />
              </div>

              <div class="mt-2 mb-2">
                <label for="inputImage" class="col-form-label">Image:</label>
                <input
                  type="text"
                  id="inputImage"
                  name="inputImage"
                  v-model="inputImage"
                  class="form-control text-center text-white"
                  aria-describedby="imageHelpBlock"
                />
                 <div id="imageHelpBlock" class="form-text">
                  Insérez ici le chemin de l'image que vous voulez insérer.
                </div>
              </div>

              <div class="mt-3 mb-3">
                <label for="inputMessageTags" class="col-form-label">Tags:</label>
                <input
                  type="text"
                  id="inputMessageTags"
                  name="inputMessageTags"
                  v-model="inputMessageTags"
                  class="form-control text-center text-white"
                />
              </div>

              <div class="mt-3 mb-3">
                <label for="inputMessage" class="col-form-label">Message:</label>
                <input
                  type="text"
                  id="inputMessage"
                  name="inputMessage"
                  v-model="inputMessage"
                  class="form-control text-center text-white"
                  aria-describedby="messageHelpBlock"
                />
                <div id="messageHelpBlock" class="form-text">
                  Must be 8-150 characters long.
                </div>
              </div>

              <div class="d-flex justify-content-center mt-2">
                <router-link :to="`/`">
                  <button class="btn btnBack text-danger m-3" type="submit"><i class="fas fa-fast-backward"></i></button>
                </router-link>

                <button class="btn btnMessageModif text-white m-3" type="submit">Modifier</button>
              </div>
            </div>
          </div>
        </form>

    </div>
    
</template>

<script>
import axios from "axios";
export default {
  name: "MessageModif",

  data() {
    return {
      errors: [],
      id: this.$route.params.id,
      inputPseudo: null,
      inputCity: null,
      inputCountry: null,
      inputMessageTitle: null,
      inputImage: null,
      inputMessageTags: null,
      inputMessage: null,
    };
  },

  methods: {
    checkEditForm: function (e) {
      e.preventDefault();

      if (
        this.inputMessageTitle &&
        this.inputImage &&
        this.inputMessageTags &&
        this.inputMessage
      ) {
        this.updateMessage();
      }

      this.errors = [];

      if (!this.inputMessageTitle) {
        this.errors.push("Le champ 'intitulé du message' est vide !");
      }
      if (!this.inputImage) {
        this.errors.push("Le champ 'image' est vide !");
      }
      if (!this.inputMessageTags) {
        this.errors.push("Le champ 'tags' est vide !");
      }
      if (!this.inputMessage) {
        this.errors.push("Le champ 'message' est vide !");
      }
    },

    getMessage(component) {
      axios
        .get(
          "https://cors-anywhere.herokuapp.com/https://crudcrud.com/api/c2659c124102448995b5072baf0c6409/message/" +
            component.id
        )
        .then(function (response) {
          console.log("message récupéré");

          let message = response.data;
          console.log(message);

          component.inputMessageTitle = message.title;
          component.inputPseudo = message.pseudo;
          component.inputCountry = message.country;
          component.inputCity = message.city;
          component.inputMessage = message.content;
          component.inputMessageTags = message.tags;
          component.inputImage = message.image;
        })
        .catch(console.log("échec récupération message"));
    },

    updateMessage() {
      let message = {
        title: this.inputMessageTitle,
        pseudo: this.inputPseudo,
        ville: this.inputCity,
        pays: this.inputCountry,
        content: this.inputMessage,
        image: this.inputImage,
        tags: this.inputMessageTags,
        date: new Date(),
      };

      axios
        .put(
          "https://cors-anywhere.herokuapp.com/https://crudcrud.com/api/c2659c124102448995b5072baf0c6409/message/" +
            this.id,
          message
        )

        .then(() => {
          alert("Message modifié");
         
        //  Ramène vers la page d'acceuil en l'actualisant
          window.location.href = "http://localhost:8080/";
        })
        .catch((error) => {
          this.error = true;
          console.log(error);
        });
    },

  },
  created() {
    this.getMessage(this);
  },
};
</script>

<style>
#contentMessageModif h3 {
  font-size: 40px;
  color: #08065f;
  font-weight: bold;
}
#contentMessageModif li {
  list-style: none;
}
#contentMessageModif .card {
  border: solid 2px #08065f;
}
#contentMessageModif .card-body label {
  font-size: 20px;
  font-weight: bold;
  color: #08065f;
}
#contentMessageModif .card-body input {
  font-size: 15px;
  background-color: #08065f;
}
.btnMessageModif {
  background-color: #08065f;
  font-size: 20px;
  font-weight: bold;
}
</style>