<script setup>
// When we use state in Vue, sometimes we want our app run if user make a change or interact with our app.accent
// For Example: We want our app not to display the data until user choose the category in the dropdown menu.
// To make this happen, we can use "Watch"; a built-in function in Vue
// Watch is a function that allows us to run a function when the state changes.

// There are 2 types if watchers in Vue: "watch" and "watchEffect"

import { ref, watch, watchEffect } from "vue";

const productID = ref("");
const product = ref(null);

const itemID = ref("item1");
const item = ref(null);

// Watch

// Watch have 3 parameters: source, callback, and options
// source: productID
// callback: a function that will run when the source changes.
// options: "immediate" & "once"
watch(productID, async (newVal, oldVal) => {
  if (newVal) {
    const response = await fetch(`/${newVal}.json`);
    product.value = await response.json();
  } else {
    product.value = null;
  }
});

watch(
  itemID,
  async (newItemVal, oldItemVal) => {
    const response = await fetch(`/${newItemVal}.json`);
    item.value = await response.json();
  },
  // options
  {
    // immediate: makes the watcher run immediately when the app runs,
    immediate: true,

    // once: makes the watcher run only once when the source changes, and then it will stop watching for changes.
    // once: true
  },
);

// WatchEffect

watchEffect(async() => {
  const response = await fetch(`/${itemID.value}.json`);
  item.value = await response.json();
})
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

  <hr />

  <label for="itemID">
    Item Id:
    <select v-model="itemID">
      <option value="item1">Item 1</option>
      <option value="item2">Item 2</option>
      <option value="item3">Item 3</option>
    </select>
  </label>

  <div v-if="item">
    <h1>Item</h1>
    <p>ID: {{ item.id }}</p>
    <p>Name: {{ item.name }}</p>
    <p>Description: {{ item.desc }}</p>
  </div>
</template>

<style scoped></style>
