<script setup>
import { computed, reactive, ref } from "vue";

const counter = ref(0);

function increment() {
  counter.value++;
  console.log("increment");
}

const person = reactive({
  name: "",
  age: "",
});

function sayHello() {
  person.name = document.getElementById("name").value;
  person.age = document.getElementById("age").value;
}

function fullName() {
  console.log("full name method");
  return `${person.name} ${person.age}`;
}

// In this scenario i give you an example of how to use methods
// Instead of you type <h1>{{ person.name }}</h1> in template, we can store that value in a method/function and then we call it in template

// Before:
// <h1>{{ person.name }} {{ person.age }}</h1>
//
// After:
// <h1>{{ fullName() }}</h1>

// But, there is unnoticed problem in here
// Everytime you click the button, that component will re-render and the method will be called again
// What if the method contains a lot of code or complex logic? That will cause performance issue
// The Process:
// 1. Input name and age
// 2. Click the button hello
// 3. fullName method will be called
// 4. tag h3 will be updated
// 5. Click increment button
// 6. Increment method will be called
// 7. "counter" value will be updated
// 8. Vue notice if the state is changed, it will re-render the component
// 9. Vue re-render template again
// 10. That will cause the method fullName() to be called again

// Vue give us a solution, we can use "computed" to solve this problem
const fullname2 = computed(() => {
  console.log("computed function called");
  return `${person.name}`;
});

// You will notice eventho you click increment button, the fullname2 will not be called again
// "Computed" will only be called when the state is changed
</script>

<template>
  <button v-on:click="increment">Counter = {{ counter }}</button>
  <div>
    <input type="text" placeholder="name" id="name" name="name" />
    <input type="number" placeholder="age" id="age" name="age" />
  </div>
  <button v-on:click="sayHello">Say hello</button>
  <h3>Hello {{ fullName() }}</h3>
  <h4>Hi {{ fullname2 }}</h4>
</template>

<style scoped></style>
