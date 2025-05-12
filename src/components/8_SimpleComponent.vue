<script setup>
import { ref } from 'vue'
import TodoItem from './8.1_TodoItem.vue'

const groceryList = ref([
  { id: 0, text: 'Vegetables' },
  { id: 1, text: 'Cheese' },
  { id: 2, text: 'Whatever else humans are supposed to eat' }
])
</script>


<template>

    <h1>8. Simple component</h1>

    <ol>
        <TodoItem v-for="item in groceryList"
        :todo="item"
        :key="item.id">
        </TodoItem>
    </ol>
</template>