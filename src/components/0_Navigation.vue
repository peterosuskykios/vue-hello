<script setup>
import { ref, computed } from 'vue';

// Import all components
import Basic from './1_Basic.vue'
import Todo from './2_Todo.vue'
import ChildComp from './3_ChildComp.vue'
import UserInput from './4_UserInput.vue'
import AttrBinding from './5_AttrBinding.vue'
import ConditionalsLoops from './6_ConditionalsLoops.vue'
import FormBindings from './7_FormBindings.vue'

// Components array
const allComponents = [
  Basic,
  Todo,
  ChildComp,
  UserInput,
  AttrBinding,
  ConditionalsLoops,
  FormBindings
  // add another
]

const currentPage = ref(1)
const perPage = 5

// Computed components for current page
const paginatedComponents = computed(() => {
  const start = (currentPage.value - 1) * perPage
  const end = start + perPage
  return allComponents.slice(start, end)
})

</script>


<template>
  <!-- Nav buttons -->
  <div>
    <button @click="currentPage = 1">1-5 </button>
    <button @click="currentPage = 2">6-10</button>
    <!-- add another if need -->
  </div>

  <!-- Show 5 components for screen -->
  <div>
    <component
      v-for="(component, index) in paginatedComponents"
      :key="index"
      :is="component"
    />
  </div>


</template>