<script setup>
import { ref, computed, onMounted, watch } from 'vue'

import Navigation  from './components/0_Navigation.vue'


const msg = ref('From parent')
const childMsg = ref('No child msg yet')

</script>

<template>
  <!-- Basic Vue stuff -->
  <Navigation />

</template>


<style>
.done {
  text-decoration: line-through;
}
</style>