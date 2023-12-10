<script setup>
import { ref } from "vue";
import NoteList from "./NoteList.vue";
const newNoteTitle = ref("");
const newNoteBody = ref("");

const createNote = () => {
  fetch("http://localhost:3000/notes/", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({
      title: newNoteTitle.value,
      body: newNoteBody.value,
    }),
  })
    .then((res) => res.json())
    .then((data) => data.value);
  resetNote();
};

const resetNote = () => {
  newNoteTitle.value = "";
  newNoteBody.value = "";
};
</script>

<template>
  <div>
    <form @submit.prevent="createNote">
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
      <button type="submit">Save</button>
    </form>
  </div>
</template>
