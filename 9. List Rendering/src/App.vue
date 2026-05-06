<script setup>
const items = [
  { id: 1, name: "Item 1", done: true },
  { id: 2, name: "Item 2", done: false },
  { id: 3, name: "Item 3", done: false },
];
</script>

<template>
  <h3>List Items</h3>

  <!-- In vue we can run looping by run the directive for -->
  <ul>
    <!-- Tips: always use directive key for loop so Vue will not re-render all items when data change -->
    <!-- with key, Vue will only re-render the items that have changed -->
    <li v-for="item in items" :key="item.id">
      {{ item.name }}
    </li>
  </ul>

  <hr />

  <!-- Vue also can loop object -->
  <ul v-for="item2 in items" :key="item2.id">
    <li v-for="(value, key) in item2">{{ key }} : {{ value }}</li>
  </ul>

  <hr />

  <!-- We can specificly tell the code how many times directive for will run -->
  <div v-for="n in 3">
    <p>Hello {{ n }}</p>
  </div>

  <hr />

  <!-- We also can use directive if for our component but directive if will be run first before directive for run -->
  <!-- better you choose 1 directive each component -->
  <!-- <ul v-for="item3 in items" :key="item3.id" v-if="!item3.done">
    <li>{{ item3.name }}</li>
  </ul> -->
</template>

<style scoped></style>
