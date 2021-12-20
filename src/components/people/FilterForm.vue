<template>
  <form action="" id="directory-filters">
    <div class="group">
      <label for="txt-name">Name:</label>
      <input
        type="text"
        name="name"
        placeholder="Name of employee"
        id="txt-name"
        v-model.trim="search.name"
        @input="notifyFilterUpdate"
      />
    </div>
    <div class="group">
      <label for="sel-title">Job Title:</label>
      <select
        name="sel-title"
        id="sel-title"
        v-model="search.title"
        @change="notifyFilterUpdate"
      >
        <option value="">- Select -</option>
        <option
          v-for="title in titles.titles"
          :key="title.key"
          :value="title.key"
        >
          {{ title.display }}
        </option>
      </select>
    </div>
    <div class="group">
      <label
        ><input
          type="checkbox"
          value="1"
          v-model="search.intern"
          @change="notifyFilterUpdate"
        />
        Intern</label
      >
    </div>
    <div class="group">
      <input type="reset" value="Reset" @click="resetFilters" />
    </div>
  </form>
</template>

<script>
import titleData from "../../assets/data/people-data";

export default {
  data() {
    return {
      titles: titleData,
      search: {
        name: "",
        title: "",
        intern: false,
      },
    };
  },
  methods: {
    notifyFilterUpdate() {
      this.$emit("filter-people", this.search);
    },
    resetFilters() {
      this.search = {
        name: "",
        title: "",
        intern: false,
      };
      this.notifyFilterUpdate();
    },
  },
};
</script> 
