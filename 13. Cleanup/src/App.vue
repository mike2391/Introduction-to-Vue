<script setup>
import WithCleanup from "./Components/WithCleanup.vue";
import WithoutCleanUp from "./Components/WithoutCleanUp.vue";
</script>

<!-- I can say this project is "Watchers Part 2" -->
<!-- When we develop an application, user might make a lot of changes in very short time -->
<!-- The "change" i talk about is "user interaction" (ex: click, type, etc) -->

<!-- Sometimes an app with websocket or other connection with backend proccess the data parallely -->
<!-- For Example: you type "macbook" in the search bar and then you click "macbook" -->
<!-- There is a running proccess that executes many times while you type "m" -> "a" -> "c" -> .... until it become "macbook"   -->

<!-- While the app proccess the change of the state value, we need to clean up the previous state -->
<!-- Or else the previous state will be overwritten, because we don't know which state value is the latest -->
<!-- "macbook" have 7 letters, so we can say if there are 7 request which run parallely, and we don't know which state will be returned -->

<!-- It can be "mac", or "macb", or "macbo", or "macboo", or "macbook" -->
<!-- Imagine while you try to type "macbook" but your online store app suggest "mouse" or "monitor" -->

<!-- Why it can be happen? There are too many variable that might affect which state value will be returned -->
<!-- Server speed, data size, cache, internet latency, etc -->

<!-- Cleanup is a way to solve this problem -->
<!-- Cleanup will delete or stop the previous state so that the latest state will be returned -->
<template>
  <!-- I give you 2 types of codes, one is without cleanup and the other one is with cleanup -->
  <WithoutCleanUp />
  <hr />
  <WithCleanup />
</template>

<style scoped></style>
