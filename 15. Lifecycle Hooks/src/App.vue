<script setup>
import { onBeforeMount, onBeforeUpdate, onMounted, onUpdated, ref } from "vue";

const isZoomed = ref(false);

function toggleZoom() {
  isZoomed.value = !isZoomed.value;
}

const word = ref("Hello World");

onBeforeMount(() => {
  console.info("before mount");
});

onMounted(() => {
  console.info("mounted");
});

onBeforeUpdate(() => {
  console.info("before update");
});

onUpdated(() => {
  console.info("updated");
});
</script>

<!-- In Vue there are so many stages in the lifecycle -->
<!-- And in every stage there is a corresponding lifecycle hook -->
<!-- For example, if we want to run a function before the component is mounted, we can use "onBeforeMount" -->
<!-- Similarly, we have hooks for other stages like "onMounted", "onBeforeUpdate", "onUpdated", etc. -->
<!-- In this example, we will log a message in each lifecycle hook to see when they are called -->

<template>
  <h1>Lifecycle Hooks</h1>
  <div class="container">
    <img class="image" style="height: 500px" src="/img/lifecycle.png" alt="Lifecycle Hooks" :class="{ zoomed: isZoomed }" @click="toggleZoom" />
  </div>
  <p>In Vue there are so many stages in the lifecycle</p>
  <ul>
    <li>beforeCreate</li>
    <li>created</li>
    <li>beforeMount</li>
    <li>mounted</li>
    <li>beforeUpdate</li>
    <li>updated</li>
    <li>beforeUnmount</li>
    <li>unmounted</li>
  </ul>

  <input type="text" v-model="word" />
  <p>{{ word }}</p>
</template>

<style scoped>
.container {
  overflow: hidden;
}

.image {
  width: 250px;
  cursor: pointer;
  transition: 0.3s ease;
}

/* Saat di-zoom */
.zoomed {
  transform: scale(2);
}
</style>
