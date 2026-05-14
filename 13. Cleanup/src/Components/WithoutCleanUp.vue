<script setup>
import { ref, watch } from "vue";

const keyword = ref("");
const result = ref("");
const loading = ref(false);

// Calling API Simulation
function fakeFetch(value, delay, signal) {
  return new Promise((resolve, reject) => {
    const timer = setTimeout(() => {
      resolve(`Search Result: ${value}`);
    }, delay);

    signal?.addEventListener("abort", () => {
      clearTimeout(timer);
      reject("Request cancelled");
    });
  });
}

/*
|--------------------------------------------------------------------------
| Without onWatcherCleanup
|--------------------------------------------------------------------------
|
| Try typing quickly:
| m -> ma -> mac -> macbook
|
| Sometimes slow requests finish last
| and overwrite the latest result.
|
*/

watch(keyword, async (newValue) => {
  if (!newValue) {
    result.value = "";
    return;
  }

  loading.value = true;

  // Random delay simulation
  const delay = Math.random() * 3000;

  try {
    const response = await fakeFetch(newValue, delay);

    console.log("Done:", newValue);

    result.value = response;
  } catch (error) {
    console.log(error);
  } finally {
    loading.value = false;
  }
});
</script>

<template>
  <div>
    <h1>Without onWatcherCleanup</h1>

    <input v-model="keyword" type="text" placeholder="Try typing quickly..." />

    <p v-if="loading">Loading...</p>

    <h3>{{ result }}</h3>

    <p>
      Try typing quickly:
      <br />
      m → ma → mac → macbook
    </p>

    <p>Look at the console: it will return unpredictable results.</p>
  </div>
</template>
