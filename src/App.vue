<script setup>
  import { ref, computed } from 'vue'
  import Todo from './components/Todo.vue'
  import Filter from './components/Filter.vue'
  import NewTodo from './components/NewTodo.vue'

  const input = ref(null)
  const todos = ref([
    {id: 0, string: 'Mimir', finished: false},
    {id: 1, string: 'Jogar LoL', finished: false},
    {id: 2, string: 'Estudar', finished: false}
  ])
  const filter = ref('All')
  
  const filteredTodos = computed(() =>{
    let filtered
    switch(true) {
      case filter.value === 'Open': {
        filtered = todos.value.filter((todo) => !todo.finished)
        break
      }
      case filter.value === 'Finished': {
        filtered = todos.value.filter((todo) => todo.finished)
        break
      }
      default: {
        const finished = todos.value.filter((todo) => todo.finished)
        const opened = todos.value.filter((todo) => !todo.finished)
        filtered = [...opened, ...finished]
      }
    }
    return filtered
  })
  
  function insertNewTodo(newTodo) {
    const id = todos.value.length
    todos.value.push({id, string: newTodo, finished: false})
  }
  function changeFilter(newFilter) {
    filter.value = newFilter
  }
</script>

<template>
  <NewTodo @insert-new-todo="insertNewTodo"/>
  <Filter @change-filter="changeFilter"/>
  <Todo :todos="filteredTodos"/>
  <p>{{ filter }}</p>
</template>