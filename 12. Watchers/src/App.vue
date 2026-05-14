<script setup>
// When we use state in Vue, sometimes we want our app run if user make a change or interact with our app.accent
// For Example: We want our app not to display the data until user choose the category in the dropdown menu.
// To make this happen, we can use "Watch"; a built-in function in Vue
// Watch is a function that allows us to run a function when the state changes.

// There are 2 types if watchers in Vue: "watch" and "watchEffect"

import { ref, watch, watchEffect } from "vue";

const productID = ref("");
const product = ref(null);

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

const itemID = ref("item1");
const item = ref(null);

watch(
  itemID,
  async (newItemVal, oldItemVal) => {
    const response = await fetch(`/${newItemVal}.json`);
    item.value = await response.json();
  },
  // options
  {
    // immediate: makes the watcher run immediately when the app runs
    // the app will not show anything eventho you already declare a default value like "const itemID = ref("item1");" if you not use "immediate: true"
    immediate: true,

    // once: makes the watcher run only once when the source changes, and then it will stop watching for changes.
    // once: true
  },
);

const stuffID = ref("stuff1");
const stuff = ref(null);

// WatchEffect
// Similar to "watch", but it runs immediately when the app runs
// watchEffect will run every time the source changes without the need to specify the source. (Vue automatically tracks the source)
watchEffect(async () => {
  const response = await fetch(`/${stuffID.value}.json`);
  stuff.value = await response.json();
});

// ********* There is 1 thing left to discuss about watchers, which is "cleanup". We will discuss it in the next chapter *********
</script>

<template>
  <!-- ============Product============= -->
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
  <!-- =============Item============= -->
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

  <hr />
  <!-- =============Stuff============= -->
  <label for="stuffID">
    Stuff Id:
    <select v-model="stuffID">
      <option value="stuff1">Stuff 1</option>
      <option value="stuff2">Stuff 2</option>
      <option value="stuff3">Stuff 3</option>
    </select>
  </label>

  <div v-if="stuff">
    <h1>Stuff</h1>
    <p>ID: {{ stuff.id }}</p>
    <p>Name: {{ stuff.name }}</p>
    <p>Description: {{ stuff.desc }}</p>
  </div>
</template>

<style scoped></style>
