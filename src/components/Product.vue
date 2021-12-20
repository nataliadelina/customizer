<template>
  <div class="cart">
    <h2>Vue Basketball Sneakers</h2>
    <p>run faster, jump higher</p>
    <div :class="['product-image', sizeClass]">
      <!-- <img :src="sizeSrc" alt="product" /> -->
      <img
        :src="require(`@/assets/images/${sizeSrc}`)"
        alt="product"
        width="300"
      />
    </div>

    <div class="selectors">
      <form class="field-group">
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
      </form>
    </div>

    <form class="field-group">
      <label for="color-options">Color:</label>
      <select
        name="colorOptions"
        id="color-options"
        v-model="selectedColor"
        @change="updateSizesByColor"
      >
        <option v-for="(color, index) in colors" :key="index">
          {{ color }}
        </option>
      </select>
    </form>
  </div>
</template>

<script>
import inventory from "../assets/data/inventory";

export default {
  data() {
    return {
      message: "Product customizer will go here",
      sizes: inventory.allSizes,
      selectedSize: 9,
      colors: inventory.allColors,
      selectedColor: "red",
    };
  },
  computed: {
    sizeClass: function () {
      return "product-size--" + this.selectedSize.toString().replace(".", "_");
    },
    sizeSrc: function () {
      //   return "../assets/images/" + this.selectedColor + ".jpg";
      return this.selectedColor + ".jpg";
    },
  },
  methods: {
    updateColorsBySize(evt) {
      // console.log("called updateColorsBySize", evt.target.value);
      // this.colors = inventory.bySize[evt.target.value];

      let selectedSize = evt.target.value,
        availableColors = inventory.bySize[selectedSize];

      this.colors = availableColors;

      // if the currently selected color isn't available in the new size,
      // set the selected color to the first available color
      if (availableColors.indexOf(this.selectedColor) === -1) {
        this.selectedColor = availableColors[0];
      }
    },
    updateSizesByColor: function (evt) {
      let selectedColor = evt.target.value,
        availableSizes = inventory.byColor[selectedColor];

      this.sizes = availableSizes;

      // if the currently selected size isn't available in the new color,
      // set the selected size to the first available size
      if (availableSizes.indexOf(this.selectedSize) === -1) {
        this.selectedSize = availableSizes[0];
      }
    },
  },
};
</script>

<style scoped>
.product-image img {
  max-width: 100%;
  transition: transform 0.5s;
}

.product-size--7 img {
  transform: scale(0.5);
}

.product-size--7_5 img {
  transform: scale(0.55);
}

.product-size--8 img {
  transform: scale(0.6);
}

.product-size--8_5 img {
  transform: scale(0.65);
}

.product-size--9 img {
  transform: scale(0.7);
}

.product-size--9_5 img {
  transform: scale(0.75);
}

.product-size--10_5 img {
  transform: scale(0.8);
}

.product-size--11 img {
  transform: scale(0.85);
}

.product-size--11_5 img {
  transform: scale(0.9);
}

.product-size--12 img {
  transform: scale(0.95);
}

.product-size--12_5 img {
  transform: scale(1);
}
</style>
