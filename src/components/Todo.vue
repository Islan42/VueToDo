<script setup>
  import { ref } from 'vue'
  
  const props = defineProps(['todos'])
  const emit = defineEmits(['remove-todo'])
  
  function changeFinished(todo) {
    todo.finished = !todo.finished
  }  
</script>

<template>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <span>
        {{ todo.string }}: {{ todo.finished }}
        <input type="checkbox" :id="`finished:${todo.id}`" @change="changeFinished(todo)" :checked="todo.finished">
        <label :for="`finished:${todo.id}`" >Dale</label>
      </span>
    </li>
  </ul>
</template>