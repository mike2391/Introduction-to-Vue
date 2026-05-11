<script setup>
import { reactive } from "vue";

const contact = reactive({
  name: "",
  email: "",
  age: 0,
  type: "Regular",
  complain: false,
  message: "",
});
</script>

<!-- When in "10. Event Handling in Vue" we declare a function to change a value everytime an event happens, in this case we use "v-model" -->
<!-- Imagine if we have a lot of input and we declare every single function for eact input then it will be a lot of code -->
<!-- "v-model" is an input binding function that allows us to directly bind the value of the input to a variable -->
<!-- But we need to know first if "v-model" will only works for some type of input -->
<!-- There are 3 type of inputs that support "v-model": input, select, and textarea -->

<template>
  <h1>Contact Us</h1>
  <form>
    <div>
      <label for="name"
        >Name:
        <input type="text" id="name" placeholder="Name" v-model="contact.name" />
      </label>
    </div>

    <div>
      <label for="email"
        >Email:
        <input type="text" id="email" placeholder="Email" v-model="contact.email" />
      </label>
    </div>

    <div>
      <label for="age"
        >Age:
        <input type="number" id="age" placeholder="Age" v-model="contact.age" />
      </label>
    </div>

    <div>
      <label for="type"
        >type:
        <select id="type" v-model="contact.type">
          <option value="Regular">Regular</option>
          <option value="VIP">VIP</option>
        </select>
      </label>
    </div>

    <div>
      <label for="complain"
        >Complain:
        <input type="checkbox" id="complain" v-model="contact.complain" />
      </label>
    </div>

    <div>
      <label for="message"
        >Message:
        <textarea id="message" v-model="contact.message"></textarea>
      </label>
    </div>
  </form>

<!-- You will see if everytime you change or input something, the value of the variable will change -->

  <h1>Preview</h1>
  <div>
    <p>Name: {{ contact.name }}</p>
    <p>Name: {{ contact.email }}</p>
    <p>Name: {{ contact.age }}</p>
    <p>Name: {{ contact.type }}</p>
    <p>Name: {{ contact.complain }}</p>
    <p>Name: {{ contact.message }}</p>
  </div>
</template>

<style scoped></style>
