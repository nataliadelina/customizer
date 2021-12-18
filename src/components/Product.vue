<template>
  <div class="cart">
    <h2>Vue Basketball Sneakers</h2>
    <p>run faster, jump higher</p>
    <div :class="['product-image', sizeClass]">
      <img src="../assets/images/red.jpg" alt="" />
    </div>

    <div class="selectors">
      <div class="field-group">
        <label for="size-options">Size:</label>
        <select
          name="sizeOptions"
          id="size-options"
          v-model="selectedSize"
          @change="updateColorsBySize"
        >
          <option v-for="(size, index) in sizes" v-bind:key="index">
            {{ size }}
          </option>
        </select>
      </div>
    </div>

    <div class="field-group">
      <label for="color-options">Color:</label>
      <select name="colorOptions" id="color-options">
        <option>Red</option>
        <option>Blue</option>
        <option>Green</option>
        <option>Brown</option>
      </select>
    </div>
  </div>
</template>

<script>
import inventory from "../assets/inventory";

console.log("inventory:", inventory);

export default {
  data() {
    return {
      message: "Product customizer will go here",
      sizes: inventory.allSizes,
      selectedSize: 9,
      colors: inventory.allColors,
    };
  },
  computed: {
    sizeClass: function () {
      return "product-size--" + this.selectedSize.toString().replace(".", "_");
    },
  },
  methods: {
    updateColorsBySize(evt) {
      console.log("called updateColorsBySize", evt.target.value);

      this.colors = inventory.bySize[evt.target.value];
    },
  },
};
</script>
