<script setup>
import { onBeforeMount, onBeforeUpdate, onMounted, onUpdated, ref } from "vue";

const isOpen = ref(false);

function openImage() {
  isOpen.value = true;
}

function closeImage() {
  isOpen.value = false;
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
<!-- I suggets you to open it in the console so u will understand when they are called -->

<template>
  <h1>Lifecycle Hooks</h1>
  <img src="/img/lifecycle.png" alt="lifecycle" class="thumbnail" @click="openImage" />

  <!-- Overlay -->
  <div v-if="isOpen" class="overlay" @click="closeImage">
    <!-- Gambar besar -->
    <img src="/img/lifecycle.png" alt="lifecycle" class="full-image" @click.stop />
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
.thumbnail {
  width: 250px;
  cursor: zoom-in;
  border-radius: 10px;
  transition: 0.3s;
}

.thumbnail:hover {
  opacity: 0.8;
}

/* Background hitam transparan */
.overlay {
  position: fixed;
  inset: 0;

  background: rgba(0, 0, 0, 0.8);

  display: flex;
  justify-content: center;
  align-items: center;

  z-index: 999;
}

/* Gambar besar */
.full-image {
  max-width: 90%;
  max-height: 90%;

  border-radius: 12px;

  animation: zoom 0.2s ease;
}

/* Animasi muncul */
@keyframes zoom {
  from {
    transform: scale(0.7);
    opacity: 0;
  }

  to {
    transform: scale(1);
    opacity: 1;
  }
}
</style>
