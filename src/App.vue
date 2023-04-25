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
    const filtered = todos.value.filter((todo) => todo.finished)
    return filtered
  })
</script>

<template>
  <form>
    <input>
    <input type="button" value="Inserir">
  </form>
  <ul>
    <li v-for="todo in filteredTodos">{{todo.string}}</li>
  </ul>
</template>