<script setup>
  import { ref } from 'vue'
  
  const props = defineProps(['todo'])
  const emit = defineEmits(['remove-todo'])
  
  function changeFinished() {
    props.todo.finished = !props.todo.finished
  }  
</script>

<template>
  <span>
    {{ todo.string }}: {{ todo.finished }}
    <input type="checkbox" :id="`finished:${todo.id}`" @change="changeFinished" :checked="todo.finished">
    <label :for="`finished:${todo.id}`" >Dale</label>
  </span>
</template>