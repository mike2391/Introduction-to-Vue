<script setup>
import { reactive, ref, useTemplateRef } from "vue";

const notes = reactive([]);
const note = ref("");
const noteInput = useTemplateRef("noteInput");

function addNote() {
  notes.push(note.value);
  note.value = "";
  noteInput.value.focus();
}
</script>

<!-- When we want to make a variable that represent an HTML element, we usually use getElementById -->
<!-- In Vue, we can use useTemplateRef to make a variable that represent an HTML element -->
<!-- We just simply type "ref" in HTML tag and Vue will detect it automatically -->
<!-- Then we access that element by using "useTemplateRef" -->

<template>
  <h1>Buat Note</h1>

  <div>
    <input type="text" ref="noteInput" v-model="note" placeholder="Tambah Note" />
    <button @click="addNote">Tambah Note</button>
  </div>
  <h1>Daftar Note</h1>
  <ul>
    <li v-for="note in notes">
      {{ note }}
    </li>
  </ul>
</template>

<style scoped></style>
