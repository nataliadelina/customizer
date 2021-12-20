<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <Product />
  <hr />
  <People />
</template>

<script>
import Product from "./components/Product.vue";
import People from "./components/people/People.vue";

export default {
  name: "App",
  components: {
    Product,
    People,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
