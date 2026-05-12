<script setup>
import { ref, watch } from "vue";

const productID = ref("");
const product = ref(null);

watch(productID, async (newVal, oldVal) => {
  if (newVal) {
    const response = await fetch(`/product${newVal}.json`);
    product.value = await response.json();
  } else {
    product.value = null;
  }
});
</script>

<template>
  <label for="productID">
    Product Id:
    <select v-model="productID">
      <option value=""></option>
      <option value="product1">Product 1</option>
      <option value="product2">Product 2</option>
      <option value="product3">Product 3</option>
    </select>
  </label>

  <div v-if="product">
    <h1>Product</h1>
    <p>ID: {{ product.id }}</p>
    <p>Name: {{ product.name }}</p>
    <p>Price: ${{ product.price.toFixed(2) }}</p>
  </div>
</template>

<style scoped></style>
