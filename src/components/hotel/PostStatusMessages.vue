<template>
  <div id="status-list">
    <ul class="messages" v-if="loaded">
      <li v-for="message in messages" :key="message.id">
        {{ message.msg }}
        <span class="name">— {{ messageTypes[message.type] }}</span>
        <span class="time">{{ timeFormatted(message.time) }}</span>
      </li>
    </ul>
    <vue-simple-spinner
      message="Loading…"
      :line-size="5"
      text-fg-color="white"
      v-else
    ></vue-simple-spinner>
  </div>
</template>

<script>
import VueSimpleSpinner from "../../assets/spinner/Spinner.vue";

export default {
  props: ["messages", "loaded"],
  components: {
    VueSimpleSpinner,
  },
  data() {
    return {};
  },
  methods: {
    timeFormatted(time) {
      var statusDate = date.parse(time, "YYYY-MM-DD, HH:mm"),
        dateFormat = "M/D/Y, h:mm A";

      return date.format(statusDate, dateFormat);
    },
  },
};
</script>