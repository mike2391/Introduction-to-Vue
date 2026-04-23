<script setup>
import { ref } from "vue";

// In Vue, we can use "ref" to create reactive state
// ref is a built-in function, and the "0" is a default value
const ReactiveCounter = ref(0);

function reactiveIncrement() {
  // We can change the value of "ReactiveCounter" by incrementing the value of the "ReactiveCounter" -> ReactiveCounter.value
  // Why we need to declare "ReactiveCounter.value++" instead of "ReactiveCounter++"?
  // Because any variable declared using ref will be wrapped in a reactive object.
  // So we can access the value of the "ReactiveCounter" by "ReactiveCounter.value"
  // You can see how the variable looks like in HTML, i've screen shot it

  ReactiveCounter.value++;
  console.info("ReactiveCounter:", ReactiveCounter);
}

// We also can make complex object
const data = ref({
  name: "John Doe",
  age: 20,
});

function addAge() {
  // data.value.age++; -> We can use this method or we change the whole object and reassign it

  data.value = {
    ...data.value,
    age: data.value.age + 1,
  };
}
</script>

<template>
  <h1 id="counter">Counter: {{ ReactiveCounter }}</h1>
  <button v-on:click="reactiveIncrement">Increment (Reactive)</button>

  <hr />
  <h2>this is how the variable "ReactiveCounter" looks like</h2>
  <img src="/img/image.png" alt="" />

  <hr />
  <h1>{{ data.name }}'s Age: {{ data.age }} Years Old</h1>
  <button v-on:click="addAge">Add {{ data.name }} Age</button>
</template>

<style scoped>
button {
  font-size: 40px;
  color: #1ce1e7;
  background-color: teal;
  cursor: pointer;
}
</style>
