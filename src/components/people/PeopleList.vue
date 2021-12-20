<template>
  <div>
    <!-- <FilterForm :people="people" /> -->
    <div class="results">
      <!-- <transition-group name="fade"> -->
      <transition-group
        enter-active-class="animated zoomIn"
        leave-active-class="animated zoomOut"
      >
        <div class="person" v-for="person in allPeople" :key="person.id">
          <h3>{{ person.name }}, {{ person.title }}</h3>
          <p>
            <img
              class="size-medium alignright"
              :src="require(`@/assets/images/${person.img}`)"
              :alt="person.name"
              width="100"
              height="100"
              sizes="(max-width: 300px) 100vw, 300px"
            />
            {{ person.bio }}
          </p>
        </div>
      </transition-group>
    </div>
  </div>
</template>

<script>
import "../../assets/animate.css";
// import peopleData from "../../assets/people-data";
// import FilterForm from "./FilterForm.vue";

export default {
  props: ["allPeople"],
  // components: {
  //   FilterForm,
  // },
  // data() {
  //   return {
  //     people: peopleData,
  //   };
  // },
  // methods: {
  //   updatePeopleList: function (params) {
  //     this.people = peopleData.filter(function (person) {
  //       return (
  //         (!params.intern || (params.intern && person.intern)) &&
  //         (params.name === "" ||
  //           person.name.toLowerCase().indexOf(params.name.toLowerCase()) !==
  //             -1) &&
  //         (params.title === "" || person.title_cat === params.title)
  //       );
  //     });
  //   },
  // },
};
</script>

<style>
/* Transition styles */

.fade-enter-active {
  opacity: 1;
  transition: opacity 500ms ease-in;
}

.fade-leave-active {
  opacity: 0.01;
  transition: opacity 500ms ease-in;
}

.fade-enter,
.fade-leave-to {
  opacity: 0.01;
}
</style>
