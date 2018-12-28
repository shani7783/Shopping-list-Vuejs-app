<template>
  <li>
    <div class="container">
      <input type="checkbox" v-model="product.complete" class="form-check-input">
      <div class="product-name" v-bind:class="{completed:product.complete}"> {{ product.text }}</div>
      <button @click="$emit('remove', product.id)"><div>x</div></button>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    product: {
      type: Object,
      required: true
    }
  }
};
</script>

<style scoped>
.container {
  display: flex;
}
  .completed {
    font-style: italic;
    text-decoration: line-through;
    color: gray;
  }
  .product-name {
    width: 90px;
  }
  button {
    width: 15px;
    height: 15px;
    font-size: 11px;
    line-height: 7px;
    margin-top: 3px;
  }
  button div {
    margin-left: -3px;
  }
  li {
    margin-bottom: 15px;
  }
  input {
    margin-top: 5px;
  }
</style>