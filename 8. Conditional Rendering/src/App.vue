<script setup>
import { ref } from "vue";

const score = ref(100);

function changeScore() {
  score.value = document.getElementById("scoreInput").value;
}
</script>

<template>
  <h1>Score App</h1>

  <input type="number" placeholder="Your Score" id="scoreInput" value="score" />
  <button v-on:click="changeScore">Change Score</button>

  <!-- In Vue we can make a conditional rendering, which means we can show a specific component if the condition is match -->
  <!-- Actually we already use a conditional rendering in "DOM Update" -->
  <!-- We can use v-if, v-else-if, and v-else to make a conditional rendering -->
  <!-- The logic is same as if-else statement in common programming language -->

  <div v-if="score > 90">
    <p>You got an A, your score is {{ score }}</p>
  </div>

  <div v-else-if="score > 70">
    <p>You got an B, your score is {{ score }}</p>
  </div>

  <div v-else>
    <p>You got an C, your score is {{ score }}</p>
  </div>
</template>

<style scoped></style>
