<script setup>
const textInterpolation = "<b>This is Text Interpolation</b>";
const RawHTML = "<b>This is Raw HTML</b>";

// You can use JS Expression in Text Interpolation
function hello() {
  return "Hello";
}
</script>

<template>
  <!-- You will see the differen between Text Interpolation and Raw HTML -->
  <!-- Text Interpolation will be render everything as plain text -->
  <!-- So if you type "<div>Hello</div>", it will be render as "<div>Hello</div>" -->
  <!-- It's for prevent HTML injection/Cross Site Scripting (XSS) -->

  <!-- But if you want your text to be rendered as HTML, you can use "v-html"  -->
  <!-- So if you type "<div>Hello</div>", it will be render as "Hello"  -->

  <div class="text">{{ textInterpolation }}</div>
  <div class="text" v-html="RawHTML"></div>

  <!-- Tips: we can use JS Expression in Text Interpolation -->
  <div class="text">{{ textInterpolation.toUpperCase() }}</div>
  <div>{{ hello() }}</div>
</template>

<style scoped>
.text {
  color: #42b983;
  font-size: 40px;
}
</style>
