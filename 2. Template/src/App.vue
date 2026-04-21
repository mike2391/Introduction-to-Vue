<script setup>
const template1 = "<b>This is Template 1</b>"
</script>

<template>
  <div class="template1">{{ template1 }}</div>
  <div v-html="template1"></div>
</template>

<style scoped>
.template1{
  color: #42b983;
}
</style>
