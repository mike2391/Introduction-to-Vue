<script setup>
import { ref } from "vue";
import Profile from "./Profile.vue";
import ObjectProps from "./ObjectProps.vue";
import Product from "./Product.vue";

const counter = ref(0);
</script>

<!-- In Vue we can pass data to our component using props/properties -->
<!-- We can use props like we declare attribute in HTML -->

<!-- Basic concept application of props like this: -->
<!-- We declare props inside a component we wanna use props -->

<!-- In Profile.vue i already declare props like this: -->
<!-- const props = defineProps(["name", "age", "favouriteGame", "counter", "favouriteSport"]); -->
<!-- For case properties with 2 words like "FavouriteSport" we can use it 2 ways: "favourite-sport" or "favouriteSport" -->

<!-- In ObjectProps i give you an example if we can declare props not only in single variable but also in object -->
<!-- const { movieName, director } = defineProps(["movieName", "director"]); -->
<!-- For object props, variable name automatically links with props with same name -->
<!-- Like movieName linked with props with name "movieName" -->

<!-- In Product component (actually in PropsValidation.vue) is an example about props with validation rules -->
<!-- const product = defineProps({
  id: {
    type: Number,
    required: true,
  },
  name: {
    type: String,
    required: true,
    validator(value, props) {
      return value.trim().length !== 0;
    },
  },
  price: {
    type: Number,
    required: true,
    validator(value) {
      return value > 0;
    },
  },
}); -->
<!-- There are a lot of validation rules that we can use -->

<template>
  <Profile name="John Doe" age="30" favouriteGame="Valorant" favourite-sport="Football" :counter="counter" />
  <Profile name="Jane Smith" age="23" favouriteGame="Fortnite" favourite-sport="Basketball" :counter="counter" />
  <button @click="counter++">Increment Counter</button>
  <hr />
  <ObjectProps movie-name="Inception" director="Christopher Nolan" />
  <Product />
</template>

<style scoped></style>
