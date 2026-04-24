<script setup>
import { ref, nextTick } from 'vue'

// We use this to control whether the input is visible or not
const showInput = ref(false)

async function showAndFocus() {
  // We set "showInput" to "true" to make the input visible
  // But at this point, Vue hasn't rendered the input yet
  // Think of it like ordering food — you placed the order, but the food isn't on the table yet
  showInput.value = true

  // So if we try to access the input right away, it will return "null"
  // Because Vue hasn't finished rendering the input yet
  console.log(document.querySelector('#myInput')) // null

  // "nextTick" is a built-in function from Vue
  // It tells Vue: "wait until you're done rendering, then continue"
  // We use "await" because nextTick returns a Promise
  await nextTick()

  // Now Vue has finished rendering, so the input is available in the DOM
  // We can safely access and manipulate the input
  console.log(document.querySelector('#myInput')) // <input id="myInput" ...>
  document.querySelector('#myInput').focus()
}
</script>

<template>
  <button @click="showAndFocus">Show Input</button>

  <!-- This input only exists in the DOM when "showInput" is true -->
  <!-- That's why we can't access it before nextTick — it doesn't exist yet -->
  <input v-if="showInput" id="myInput" placeholder="I'm focused automatically!" />
</template>