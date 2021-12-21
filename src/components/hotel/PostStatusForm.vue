<template>
  <div id="post-status">
    <form @submit="postUpdate">
      <h3>Post an Update</h3>
      <div class="field-group">
        <label for="txt-message">Message</label>
        <textarea id="txt-message" rows="2" v-model="message"></textarea>
      </div>
      <div class="field-group">
        <label for="txt-type">Type</label>
        <select id="txt-type" v-model="type">
          <!-- <option v-for="(label, value) in messageTypes" :value="value"> -->
          <option
            v-for="(label, value) in messages"
            :value="value"
            :key="label.id"
          >
            {{ label }}
          </option>
        </select>
      </div>
      <div class="field-group action">
        <input type="submit" value="Post Update" />
      </div>
    </form>
  </div>
</template>

<script>
// obvs want to update this!
// let CONFIG = {
//   apiUrl: "http://localhost/status_api",
//   messageTypes: {
//     management: "Management",
//     dining: "Dining Services",
//     ops: "Operations",
//     plumbing: "Plumbing",
//     pool: "Pool",
//   },
// };

import hotelData from "../../assets/data/hotel-messages";

export default {
  data() {
    return {
      //   messageTypes: CONFIG.messageTypes,
      //   type: Object.keys(CONFIG.messageTypes)[0],
      messages: hotelData,
      message: "",
    };
  },
  methods: {
    postUpdate(evt) {
      evt.preventDefault();

      // collect data message
      //   let newStatus = {
      //     msg: this.message,
      //     type: this.type,
      //     time: date.format(new Date(), "YYYY-MM-DD, HH:mm"),
      //   };

      //   axios.post(CONFIG.apiUrl + "/post.php", newStatus).then(
      //     function (response) {
      //       if (response.data.success) {
      //         // Message received by the API - update our UI
      //         this.$emit("add-message", newStatus);
      //       }
      //     }.bind(this)
      //   );
    },
  },
};
</script>