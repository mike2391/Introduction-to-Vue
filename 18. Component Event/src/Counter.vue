<script setup>
const { counter, name, increment } = defineProps({
  counter: Number,
  name: String,
  increment: Number,
});

const emit = defineEmits(["click"]);
</script>

<template>
  <h1>Counter: {{ counter }} - Name: {{ name }}</h1>
  <button @click="emit('click', increment)">increment {{ name }}</button>
</template>

<style scoped></style>
