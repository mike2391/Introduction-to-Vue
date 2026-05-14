<script setup>
import { ref, watch, onWatcherCleanup } from "vue";

const keyword = ref("");
const result = ref("");
const loading = ref(false);

// Calling API Simulation
function fakeFetch(value, delay, signal) {
  return new Promise((resolve, reject) => {
    const timer = setTimeout(() => {
      resolve(`Search Result: ${value}`);
    }, delay);

    signal.addEventListener("abort", () => {
      clearTimeout(timer);
      reject("Request cancelled");
    });
  });
}

/*
|--------------------------------------------------------------------------
| With onWatcherCleanup
|--------------------------------------------------------------------------
|
| When watcher run again:
| - The previous request will be aborted.
|
| So only the latest request will be executed.
|
*/

watch(keyword, async (newValue) => {
  if (!newValue) {
    result.value = "";
    return;
  }

  loading.value = true;

  const controller = new AbortController();

  // CLEANUP
  onWatcherCleanup(() => {
    controller.abort();
    console.log("Old request aborted");
  });

  // Simulasi delay random
  const delay = Math.random() * 3000;

  try {
    const response = await fakeFetch(newValue, delay, controller.signal);

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
    <h1>With onWatcherCleanup</h1>

    <input v-model="keyword" type="text" placeholder="Try typing quickly..." />

    <p v-if="loading">Loading...</p>

    <h3>{{ result }}</h3>

    <p>
      Try typing quickly:
      <br />
      m → ma → mac → macbook
    </p>

    <p>Now only the latest request will be allowed to complete.</p>
  </div>
</template>
