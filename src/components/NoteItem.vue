<script setup>
  import { ref } from 'vue'

  const props = defineProps({
    note: Object
  })


</script>

<template>
  <ul>
    <li>{{ props.note.title }}</li>
    <li>{{ props.note.body }}</li>
  </ul>
</template>
