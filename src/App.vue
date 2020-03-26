<template>
  <div id = "app">
    <MessagesList :messages="$store.state.messages" />
    <MessageForm v-on:send-message="sendMessage" />
  </div>
</template>

<script>
import MessagesList from "./components/MessagesList.vue";
import MessageForm from "./components/MessageForm.vue"



export default {
  name: 'App',
  components: {MessagesList,MessageForm},
  data: () => ({
    messages: [],
  }),
  mounted: function () {
    setInterval(this.receiveMessages, 1000);
  },
  methods: {
    receiveMessages: function () {
      this.$store.dispatch("receiveMessages");
    },
    sendMessage: function (messageObj) {
      this.$store.dispatch("sendMessage", messageObj);
    },
  }
}
</script>