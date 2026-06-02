<script setup>
import { ref, watchEffect } from "vue";
import ProductDetail from "./PropsValidation.vue";

const stuffID = ref("stuff1");
const stuff = ref(null);

watchEffect(async () => {
  const response = await fetch(`/${stuffID.value}.json`);
  stuff.value = await response.json();
});
</script>

<template>
  <label for="stuffID">
    Stuff Id:
    <select v-model="stuffID">
      <option value="stuff1">Product 1</option>
      <option value="stuff2">Product 2</option>
      <option value="stuff3">Product 3</option>
    </select>
  </label>

  <div v-if="stuff">
    <ProductDetail :id="stuff.id" :name="stuff.name" :price="stuff.price" />
  </div>
</template>

<style scoped></style>
