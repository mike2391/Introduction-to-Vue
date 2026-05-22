<script setup>
import Counter from "./components/Counter.vue";
</script>

<!-- In this session i will talk about state scope in multiple components -->
<!-- Simple, every state in each component is unique -->
<!-- So eventho they have the same name, each component has it's own state -->

<!-- You can see the example in component "Counter" -->
<!-- Counter 1 and Counter 2 have their own state, so eventho you click the button in Counter 1, it will not affect the state of Counter 2 -->
<template>
  <h1>Counter 1</h1>
  <Counter />
  <h1>Counter 2</h1>
  <Counter />
</template>

<style scoped></style>
