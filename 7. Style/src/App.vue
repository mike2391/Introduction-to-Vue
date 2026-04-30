<script setup>
import { ref } from "vue";

// reactive variables to control class toggling
const red = ref(false);
const bold = ref(false);

function toggleRed() {
  red.value = !red.value;
}
function toggleBold() {
  bold.value = !bold.value;
}

// We can also define styles as objects and bind them to elements using the :style directive
const style1 = {
  color: "magenta",
};

const style2 = {
  textTransform: "uppercase",
  fontWeight: "bold",
};
</script>

<template>
  <!-- apply class dynamically based on boolean values -->
  <!-- if red = true → class "red" is applied -->
  <!-- if bold = true → class "bold" is applied -->
  <h1 :class="{ red: red, bold: bold }">Style</h1>

  <!-- static class (always applied, no condition) -->
  <h1 :class="['red', 'bold']">Style</h1>
  <button v-on:click="toggleRed">Red</button>
  <button v-on:click="toggleBold">Bold</button>

  <hr />

  <!-- apply style using v-bind:style / :style -->
  <h1 :style="style1">Magenta</h1>
  <h1 :style="[style1, style2]">Bold and Uppercase</h1>
</template>

<!-- Scoped means that this style will only apply to this component, will not affect other components -->
<style scoped>
.red {
  color: red;
}

.bold {
  text-transform: uppercase;
  font-weight: bold;
}
</style>
