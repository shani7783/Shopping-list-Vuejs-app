<template>
  <div>
    <h4>
      <label v-on:click="showComplete = !showComplete">
        <!-- The v-model attribute causes the checkdness of this box to always mirror the application's state  -->
        <input type="checkbox" v-model="showComplete">
        Show Completed
      </label>
    </h4>
    <input type="text" class="input" placeholder="New product" v-model="newProductText" @keydown.enter="addProduct">
    <ol v-if="filterProducts && filterProducts.length > 0">
      <ShoppingListItem
        v-for="product in filterProducts"
        v-bind:key="product.id"
        v-bind:product="product"
        @remove="removeProduct"
      />
    </ol>
    <p v-else>Nothing left in the list. Add a new product in the input above.</p>
  </div>
</template>

<script>

import ShoppingListItem from "./ShoppingListItem.vue";

let nextProductId = 1;

export default {
  components: {
    ShoppingListItem
  },
  data() {
    return {
      newProductText: "",
      showComplete: true,
      products: [
        {
          id: nextProductId++,
          text: "Bread",
          complete: false
        },
        {
          id: nextProductId++,
          text: "Milk 3%",
          complete: false
        },
        {
          id: nextProductId++,
          text: "Fruits",
          complete: false
        }
      ]
    };
  },
  computed: {
    filterProducts() {
      return this.products.filter(product =>
        this.showComplete ? true : !product.complete
      );
    }
  },
  methods: {
    addProduct() {
      if (this.newProductText) {
        this.products.push({
          id: nextProductId++,
          text: this.newProductText,
          complete: false
        });
        this.newProductText = "";
      }
    },
    removeProduct(idToRemove) {
      this.products = this.products.filter(product => {
        return product.id !== idToRemove;
      });
    }
  }
};
</script>

<style scoped>
  .input {
    width: 100%;
    padding: 8px 10px;
    border: 1px solid #32485f;
  }
</style>