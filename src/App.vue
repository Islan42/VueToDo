<script setup>
  import { ref, computed } from 'vue'
  import Todo from './components/Todo.vue'
  import Filter from './components/Filter.vue'

  const input = ref(null)
  const todos = ref([
    {id: 0, string: 'Mimir', finished: false},
    {id: 1, string: 'Jogar LoL', finished: false},
    {id: 2, string: 'Estudar', finished: false}
  ])
  const filteredTodos = computed(() =>{
    const filtered = todos.value.filter((todo) => todo.finished)
    return filtered
  })
  const filter = ref('All')
  const newTodo = ref('')
  
  function insertNewTodo() {
    const id = todos.value.length
    todos.value.push({id, string: newTodo.value, finished: false})
    newTodo.value = ''
    input.value.focus()
  }
  function changeFilter(newFilter) {
    filter.value = newFilter
  }
</script>

<template>
  <form @submit.prevent="insertNewTodo">
    <input v-model="newTodo" placeholder="A fazer" ref="input">
    <input type="submit" value="Inserir">
  </form>
  <Filter @change-filter="changeFilter"/>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <Todo :todo="todo"/>
    </li>
  </ul>
  <p>{{ filter }}</p>
</template>