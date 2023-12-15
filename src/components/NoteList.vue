<script setup>
import { ref } from "vue";
import NoteFormOld from "./NoteFormOld.vue";

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
      <div
      v-for="note in notes" :key="note.id">
        {{ note.title }}
        <br />
        {{ note.body }}
      </div>
  </div>
</template>
