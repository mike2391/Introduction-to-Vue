<script setup>
// We declare props by using defineProps function, the result of defineProps is an object.
const props = defineProps(["name", "age", "favouriteGame", "counter", "favouriteSport"]);
</script>

<template>
  <h1>Name : {{ props.name }}</h1>
  <h1>Age : {{ props.age }}</h1>
  <h1>Favourite Game : {{ props.favouriteGame }}</h1>
  <h1>Favourite Sport : {{ props.favouriteSport }}</h1>
  <h3>Counter : {{ props.counter }}</h3>
  <hr />
</template>

<style scoped></style>
