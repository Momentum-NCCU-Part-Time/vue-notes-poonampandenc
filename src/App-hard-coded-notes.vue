<script setup>
const notes = [
    {
      "id": 1,
      "title": "Sample note",
      "body": "This is the body of my note",
      "updatedAt": "2018-01-01T00:00:00.000Z"
    },
    {
      "id": 2,
      "title": "Sample note 2",
      "body": "This is the body of my note 2",
      "updatedAt": "2018-01-01T00:00:00.000Z"
    }
  ]
</script>

<template>
  <div>
    <h1>Vue Notes</h1>
    <ul>
    <li v-for="note in notes">
  {{ note.title }} 
  {{ note.body }}
</li>
</ul>
  </div>
  <div>
    <form>
      <div class="form-example">
        <label for="title">Note title</label>
        <input type="text" name="title" id="title" required />
      </div>
    </form>
  </div>
</template>

<style scoped>
</style>
