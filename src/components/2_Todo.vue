<script setup>
import { ref, computed, watch } from 'vue'

const hideCompleted = ref(false)

let id          = 0
const newTodo   = ref('')
const todos     = ref([
  {id: id++, text: 'Learn HTML', done: false},
  {id: id++, text: 'Learn JS', done: false},
  {id: id++, text: 'Learn Vue', done: false}
])

const filteredTodos = computed(() => {
  return hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
})

const todoId = ref(1)
const todoData = ref(null)

async function fetchData() {
  todoData.value = null
  const res = await fetch(
    `https://jsonplaceholder.typicode.com/todos/${todoId.value}`
  )
  todoData.value = await res.json()
}

fetchData()
watch(todoId, fetchData)

function addTodo() {
  const text = newTodo.value.trim()

  if (text) {
    todos.value.push({ id: id++, text: text, done: false})
    newTodo.value = ''
  }
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}

</script>

<template>
    <h1>2. TODO list</h1>
    <form @submit.prevent="addTodo">
    <input v-model="newTodo" required placeholder="new todo">
    <button>Add Todo</button>
  </form>
  <ul>
    <li v-for="todo in filteredTodos" :key="todo.id">
      <input type="checkbox" v-model="todo.done">
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>

  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? 'Show all' : 'Hide completed' }}
  </button>

  <p>Todo id: {{ todoId }}</p>
  <button @click="todoId++" :disabled="!todoData">Fetch next todo</button>
  <p v-if="!todoData">Loading...</p>
  <pre v-else>{{ todoData }}</pre>

</template>

<style>
.done {
  text-decoration: line-through;
}
</style>