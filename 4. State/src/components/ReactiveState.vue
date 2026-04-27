<script setup>
import { reactive, ref } from "vue";

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

// Vue recommends you to use "reactive" insteaf of "ref" if you want to use object data type
// the different between reactive and ref is reactive is only support object type (object, array, collection, etc)
const person = reactive({
  firstname: "",
  lastname: "",
});

// Abit different between how you change value in ref and reactive

// for "ref" we can directly change the value or even reassign the whole object
// ex:
// const user = ref({ name: 'A' })
// user.value = { name: 'B' } ✅

// for "reactive" we can only change the value in the object, we cannot reassign the whole object
// const user = reactive({ name: 'A' })
// user = { name: 'B' } ❌

function sayHello() {
  person.firstname = document.getElementById("firstname").value;
  person.lastname = document.getElementById("lastname").value;
}
</script>

<template>
  <h2 id="counter">Counter: {{ ReactiveCounter }}</h2>
  <button v-on:click="reactiveIncrement">Increment (Reactive)</button>

  <hr />
  <h2>this is how the variable "ReactiveCounter" looks like</h2>
  <img src="/img/image.png" alt="" />

  <hr />
  <h2>{{ data.name }}'s Age: {{ data.age }} Years Old</h2>
  <button v-on:click="addAge">Add {{ data.name }} Age</button>
  <hr />
  <input type="text" id="firstname" name="firstname" placeholder="firstname" />
  <input type="text" id="lastname" name="lastname" placeholder="lastname" />
  <button v-on:click="sayHello">say hello</button>
  <h3>Hello {{ person.firstname }} {{ person.lastname }}</h3>
</template>

<style scoped>
button {
  font-size: 30px;
  color: #1ce1e7;
  background-color: teal;
  cursor: pointer;
}
</style>
