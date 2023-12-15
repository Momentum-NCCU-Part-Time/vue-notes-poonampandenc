<script setup>
import { ref } from "vue";
import NoteForm from "./NoteForm.vue";

const notes = ref([]);
fetch("http://localhost:3000/notes/", {
  method: "GET",
  headers: { "Content-Type": "application/json" },
})
  .then((res) => res.json())
  .then((data) => {
    notes.value = data;
  });

const addNoteToList = (note) => {
  notes.value = [...notes.value, note];
  // notes.value.push(note);
};
</script>

<template>
  <NoteForm @note-created="addNoteToList" />
  <div class="listOfNotes">
    <h2>All Notes</h2>
    <ul v-for="note in notes" :key="note.id">
      {{
        note.title
      }}
      <br />
      {{
        note.body
      }}
    </ul>
  </div>
</template>
