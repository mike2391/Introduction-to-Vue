<script setup>
import { ref } from "vue";
import Counter from "./Counter.vue";

const counter = ref(0);

function incrementCounter(value) {
  counter.value += value;
}
</script>

<template>
  <Counter name="Counter 1" :counter="counter" :increment="1" @click="incrementCounter(1)" />
  <Counter name="Counter 2" :counter="counter" :increment="2" @click="incrementCounter(2)" />
</template>

<style scoped></style>
