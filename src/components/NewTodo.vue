<script setup>
import { ref } from 'vue'

const emit = defineEmits(['insert-new-todo'])

const newTodo = ref('')
const input = ref(null)

function insertNewTodo() {
  emit('insert-new-todo', newTodo.value)
  newTodo.value = ''
  input.value.focus()
}
</script>

<template>
  <form @submit.prevent="insertNewTodo">
    <input v-model="newTodo" placeholder="A fazer" ref="input">
    <input type="submit" value="Inserir">
  </form>
</template>