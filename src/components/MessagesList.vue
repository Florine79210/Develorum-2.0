<template>
  <div v-if="$route.path == '/'" class="container" id="messagesList">
    <li class="list-unstyled" v-for="message in messages" :key="message.id">
      <Message
        :id="message._id"
        :pseudo="message.pseudo"
        :city="message.city"
        :country="message.country"
        :title="message.title"
        :tags="message.tags"
        :image="message.image"
        :content="message.content"
        :date="message.date"
      />
    </li>
  </div>
  <div v-else><router-view :key="$route.fullPath"></router-view></div>
</template>

<script>
import Message from "./Message.vue";

export default {
  name: "MessagesList",
  props: ["messages"],
  components: {
    Message,
  },
};
</script>

<style>
</style>