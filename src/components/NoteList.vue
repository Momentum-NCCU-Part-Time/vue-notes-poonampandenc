<script setup>
import { ref } from "vue";
import NoteForm from "./NoteForm.vue";
import NoteItem from './NoteItem.vue';

const notes = ref([]);

fetch("http://localhost:3000/notes/", {
  method: "GET",
  headers: { "Content-Type": "application/json" },
  }).then((res) => res.json()).then((data) => (notes.value = data));

const addNoteToList = (note) => {
  notes.value = [...notes.value, note];
};
</script>

<template>
  <NoteForm @noteCreated="addNoteToList" />
  <div class="listOfNotes">
    <h2>All Notes</h2>
      <NoteItem v-for="note in notes" :key="note.id" :note="note"/>
  </div>
</template>
