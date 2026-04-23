<script setup>
// In Vue we can save state (data) in our component
// We can use common method to save state or modify state
// In this case we will use common method -> Document Object Manipulation
let counter = 0;

function increment() {
  counter++;
  document.getElementById("counter").innerHTML = "Counter: " + counter;
}
// It's common right? We change the value of "counter" manually
// This method is not re-rendering the component and it's not reactive and not recommended
// We will use another method to use state in Vue. We will use "reactive state"
// You can see an example of reactive state in compoonent "ReactiveState"
</script>

<template>
  <h1 id="counter">Counter: {{ counter }}</h1>
  <!-- In Vue, we can use "v-on" to add event listener -->
  <button v-on:click="increment">Increment</button>
</template>

<style scoped>
button {
  font-size: 40px;
  color: #1ce1e7;
  background-color: teal;
  cursor: pointer;
}
</style>
