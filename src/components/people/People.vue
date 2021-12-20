<template name="component-name">
  <div>
    <h2>Company Directory</h2>
    <p>
      Learn more about each person at Leaf and Mortar in this company directory.
    </p>
    <filter-form @filter-people="updatePeopleList"></filter-form>
    <people-list :all-people="people"></people-list>
    <!-- <PeopleList :al-pPeople="people" /> -->
  </div>
</template>

<script>
import peopleData from "../../assets/data/people-data";
import PeopleList from "./PeopleList.vue";
import FilterForm from "./FilterForm.vue";

export default {
  components: {
    FilterForm,
    PeopleList,
  },
  data() {
    return {
      people: peopleData.people,
    };
  },
  methods: {
    updatePeopleList: function (params) {
      this.people = peopleData.people.filter(function (person) {
        return (
          (!params.intern || (params.intern && person.intern)) &&
          (params.name === "" ||
            person.name.toLowerCase().indexOf(params.name.toLowerCase()) !==
              -1) &&
          (params.title === "" || person.title_cat === params.title)
        );
      });
    },
  },
};
</script>
