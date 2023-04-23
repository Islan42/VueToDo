<script setup>
  import { ref, computed } from 'vue'
  
  //const state = reactive({ todos:  })
  //const todos = ref(['Mimir', 'Jogar LoL', 'Estudar'])
  const todos = ref([
    {id: 0, string: 'Mimir', finished: false},
    {id: 1, string: 'Jogar LoL', finished: false},
    {id: 2, string: 'Estudar', finished: false}
  ])
  const filteredTodos = computed(() =>{
    const filtered = []
    return filtered
  })
</script>

<template>
  <form>
    <input>
    <input type="button" value="Inserir">
  </form>
  <ul>
    <li>{{todos[1].string}}</li>
    <li>B</li>
    <li>C</li>
  </ul>
</template>