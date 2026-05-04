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

  <!-- we also can use v-show too -->
  <div v-show="score > 90">Your score is {{ score }}</div>

  <!-- the different between those 2 conditional rendering is: -->
  <!-- v-if will only render the component if the condition is true/match -->
  <!-- v-show will still get rendered even if the condition is false/not match but Vue will change the CSS display property to "none" -->
</template>

<style scoped></style>
