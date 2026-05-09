<script setup>
import { computed, reactive, ref } from "vue";

const person = reactive({
  firstName: "",
  lastName: "",
});

const counter = ref(0);

function changeFirstName() {
  person.firstName = document.getElementById("firstName").value;
}

// Btw, we can use event argument too
function changeLastName(event) {
  person.lastName = event.target.value;
}

const fullName = computed(() => {
  return `${person.firstName} ${person.lastName}`;
});
</script>

<template>
  <h1>Input your Name</h1>

  <!-- In Vue we can use Event Handler. Almost all of JavaScript event handler are included in Vue -->
  <!-- We can use event handle in 2 ways -->
  <!-- 1. v-on:(event_handler_name) -->
  <!-- 2. @(event_handler_name) -->

  <input type="text" id="firstName" placeholder="First Name" v-on:input="changeFirstName" />
  <br />
  <input type="text" id="lastName" placeholder="Last Name" @input="changeLastName" />
  <br />
  <h3>Hellow, {{ person.firstName }} {{ person.lastName }}</h3>
  <hr />

  <!-- We also can use inline statement for some simple method -->

  <button @click="counter++">clicked {{ counter }}</button>

  <!-- In Vue we also can use event modifier, such as "preventDefault", etc. -->
  <!-- But instead of we declare it manually inside the function, we can use it right next to event handler name -->
  <!-- ex: @click.prevent -->
  <form action="">
    <button @click.prevent>submit</button>
  </form>

  <!-- There are 3 event modifier in Vue: Event Modifier, Key Modifier, Modifier -->
  <!-- https://vuejs.org/guide/essentials/event-handling.html#event-modifiers  -->
  <!-- https://vuejs.org/guide/essentials/event-handling.html#key-modifiers  -->
  <!-- https://vuejs.org/guide/essentials/event-handling.html#mouse-button-modifiers -->
</template>

<style scoped></style>
