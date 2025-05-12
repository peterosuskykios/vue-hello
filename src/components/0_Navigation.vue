<script setup>
import { ref, computed } from 'vue';

// Import all components
import Basic from './01_Basic.vue'
import Todo from './02_Todo.vue'
import ChildComp from './03_ChildComp.vue'
import UserInput from './04_UserInput.vue'
import AttrBinding from './05_AttrBinding.vue'
import ConditionalsLoops from './06_ConditionalsLoops.vue'
import FormBindings from './07_FormBindings.vue'
import SimpleComponent from './08_SimpleComponent.vue'
import MarkdownEditor from './09_MarkdownEditor.vue';
import FetchData from './10_FetchData.vue'
import GridWithSort from './11_GridWIthSort.vue'

// Components array
const allComponents = [
  Basic,
  Todo,
  ChildComp,
  UserInput,
  AttrBinding,
  ConditionalsLoops,
  FormBindings,
  SimpleComponent,
  MarkdownEditor,
  FetchData,
  GridWithSort
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
    <button @click="currentPage = 3">11-15</button>

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