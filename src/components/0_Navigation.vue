<script setup>
import { ref, computed } from 'vue';

// Importuj všetky komponenty
import Basic from './1_Basic.vue'
import Todo from './2_Todo.vue'
import ChildComp from './3_ChildComp.vue'
import UserInput from './4_UserInput.vue'
import AttrBinding from './5_AttrBinding.vue'
import ConditionalsLoops from './6_ConditionalsLoops.vue'

// Pole všetkých komponentov
const allComponents = [
  Basic,
  Todo,
  ChildComp,
  UserInput,
  AttrBinding,
  ConditionalsLoops
  // pridaj ďalšie podľa potreby
]

// Aktuálna stránka
const currentPage = ref(1)
const perPage = 5

// Výpočet komponentov pre danú stránku
const paginatedComponents = computed(() => {
  const start = (currentPage.value - 1) * perPage
  const end = start + perPage
  return allComponents.slice(start, end)
})

</script>


<template>
  <!-- Navigačné tlačidlá -->
  <div>
    <button @click="currentPage = 1">1-5 </button>
    <button @click="currentPage = 2">6-10</button>
    <!-- pridaj ďalšie podľa potreby -->
  </div>

  <!-- Zobraz iba komponenty aktuálnej stránky -->
  <div>
    <component
      v-for="(component, index) in paginatedComponents"
      :key="index"
      :is="component"
    />
  </div>


</template>