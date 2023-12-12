<script setup>
import { ref } from "vue";
const newNoteTitle = ref("");
const newNoteBody = ref("");
const emit = defineEmits(["noteCreated"]);

const resetNote = () => {
  newNoteTitle.value = "";
  newNoteBody.value = "";
};

const createNote = () => {
  if (!newNoteTitle) return;
  fetch("http://localhost:3000/notes/", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({
      title: newNoteTitle.value,
      body: newNoteBody.value
    })
  }).then((res) => res.json())
    .then((note) => {
      console.log("hitting .then")
      emit("noteCreated", note)
      resetNote()
    });
};

</script>

<template>
    <form id="NoteForm" @submit.prevent="createNote">
      <h2>New Note</h2>
      <div class="title">
        <input
          type="text"
          v-model.trim="newNoteTitle"
          placeholder="New Note Title"
        />
      </div>
      <br />
      <div class="body">
        <input
          type="text"
          v-model.trim="newNoteBody"
          placeholder="New Note Body"
        />
      </div>
      <button type="submit" :disabled="!newNoteTitle">Add Note</button>
    </form>
</template>
