<template>
  <PostStatusForm @add-message="addMessage" />
  <!-- <PostStatusMessages :messages="messages" :loaded="loaded" /> -->
  <PostStatusMessages :data="data" :loaded="loaded" />
</template>

<script>
import hotelData from "../../assets/data/hotel-messages";
import PostStatusMessages from "./PostStatusMessages.vue";
import PostStatusForm from "./PostStatusForm.vue";

export default {
  components: {
    PostStatusForm,
    PostStatusMessages,
  },
  data() {
    return {
      data: hotelData,
      //   messages: [],
      loaded: false,
    };
  },
  created() {
    this.retrieveStatusMessages();
  },
  methods: {
    retrieveStatusMessages() {
      //   axios
      //     .get(CONFIG.apiUrl + "/get.php?delay=3")
      //     .then(
      //       function (response) {
      //         this.messages = response.data;
      //         this.loaded = true;
      //       }.bind(this)
      //     )
      //     .catch(function (error) {
      //       console.error("retrieveStatusMessages failed", error.toString());
      //     });
    },

    addMessage(newStatus) {
      // this.retrieveStatusMessages();
      //   update messages directly
      //   this.messages.push(newStatus);
    },
  },
};
</script>