<script setup>
const helloText = "Hello World";
const classHello = "hello";
const id = "helloElement";
const buttonBoolean = true;
const data = {
  class: "dataHello",
  id: "dataHello",
};
</script>

<template>
  <!-- In Vue, we can add attribute using "v-bind" -->
  <!-- There are several ways to add attribute -->
  <!-- 1. Add attribute using "v-bind" -->
  <!-- 2. Add attribute using ":" -->

  <!-- this element using "v-bind" -->
  <div v-bind:class="classHello" v-html="helloText"></div>

  <!-- This element using ":" -->
  <!-- This is special case -->
  <!-- If your variable name is same as your attribe name, you can use ":" and you don't need to declare the variable name -->
  <!-- So instead of you type ":id=id" you can just type ":id" -->
  <div :id v-html="helloText"></div>

  <!-- we can add boolean attribute too -->
  <button :disabled="buttonBoolean">This is Button</button>

  <!-- You also can add multiple attribute by declare the object variable -->
  <!-- This element have class="dataHello" and id="dataHello" because we already declare variable object named "data" with class="dataHello" and id="dataHello" -->
  <div v-bind="data">Multiple Attribute</div>

  <!-- We also can use object specific value for our attribute -->
  <!-- This element have class="dataHello" because we call specific value from variable object "data" with key "class" which the value is "dataHello" -->
  <div :class="data.class">This Element got class from object</div>
</template>

<style scoped>
.hello {
  color: #42b983;
  font-size: 50px;
  font-weight: bold;
}

#helloElement {
  color: #005730;
  font-size: 50px;
  font-weight: bold;
}

button {
  font-size: 30px;
}

.dataHello {
  color: #1ce1e7;
  font-size: 50px;
  font-weight: bold;
}

#dataHello {
  text-decoration: underline;
}
</style>
