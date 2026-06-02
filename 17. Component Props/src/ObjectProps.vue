<script setup>
const { movieName, director } = defineProps(["movieName", "director"]);
</script>

<template>
  <h1>{{ movieName }}</h1>
  <p>Directed by {{ director }}</p>
  <hr />
</template>

<style scoped></style>
