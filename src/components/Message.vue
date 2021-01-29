<template>
  <div id="message" class="container mt-4">
    <div class="row justify-content-center">
      <div class="card ps-0 pe-0">
        <div class="card-header">
          <h4 class="card-title pt-2 pb-2 text-info">{{ title }}</h4>
          <h5 class="card-subtitle pb-2 text-white">
            <span>Posté par {{ pseudo }} </span> &emsp; le
            {{ moment(date).format("DD.MM.YYYY &ensp; à HH:mm") }}
          </h5>
        </div>

        <div class="card-body">
          <img :src="image">
          <p class="card-text">{{ content }}</p>
        </div>

        <div class="card-footer d-flex justify-content-evenly">

          <router-link :to="`/MessageModif/${id}`">
          <button
            id="btnModif"
            class="pt-1 pe-2 ps-2 bg-white border-warning"
            type="button"
          >
            <i class="fas fa-pencil-alt text-warning"></i>
          </button>
          </router-link>

          <button
            v-on:click="deleteMessage(id)"
            id="btnSupp"
            class="pt-1 pe-2 ps-2 bg-white border-danger"
            type="submit"
            method="delete"
          >
            <i class="fas fa-trash-alt text-danger"></i>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import moment from "moment";
import axios from "axios";

export default {
  name: "Message",
  props: ["id", "pseudo", "city", "coutry", "title", "content", "image", "tags", "date"],

  created: function () {
    this.moment = moment;
  },

  data() {
    return {
      message: [],
      error: false,
    };
  },

  methods: {
    deleteMessage(messageId) {
      console.log("id" + messageId);
      axios
        .delete(
          "https://cors-anywhere.herokuapp.com/https://crudcrud.com/api/f725367c785a421bb14e38e90ec6037c/message/" +
            messageId
        )

        .then(() => {
          alert("Message supprimé");
          location.reload();
        })
        .catch((error) => {
          this.error = true;
          console.log(error);
        });
    },
  },
};
</script>

<style scoped>
#message .card {
  border: outset 3px #08065f;
  border-radius: 6px;
}
#message .card-header {
  background-color: #08065f;
}
#message h4 {
  font-size: 30px;
}
#message h5 span {
  font-weight: bold;
}
#message .card-body {
  color: #08065f;
}
img {
  width: 30vw;
  max-width: 150px;
}
#message .card-footer {
  background-color: #08065f;
}
i {
  font-size: 20px;
}

</style>