<script setup>
import { ref, computed, onMounted, watch } from 'vue'

import Basic1  from './components/Basic1.vue'
import Todo  from './components/Todo.vue'
import ChildComp  from './components/ChildComp.vue'

const msg = ref('From parent')
const childMsg = ref('No child msg yet')

</script>

<template>
  <!-- Basic Vue stuff -->
  <Basic1 />

  <!-- TODO list -->
  <Todo />

  <!-- Send data betweend child and parent -->
  <ChildComp @response="(msg) => childMsg = msg", :msg="msg" >Message: {{ msg }}</ChildComp>

  <p> {{ childMsg }} </p>

</template>


<style>
.done {
  text-decoration: line-through;
}
</style>