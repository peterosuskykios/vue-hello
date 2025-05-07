<script setup>
import { ref, computed, onMounted, watch } from 'vue'

import Basic  from './components/1_Basic.vue'
import Todo  from './components/2_Todo.vue'
import ChildComp  from './components/3_ChildComp.vue'
import UserInput  from './components/4_UserInput.vue'

const msg = ref('From parent')
const childMsg = ref('No child msg yet')

</script>

<template>
  <!-- Basic Vue stuff -->
  <Basic />

  <!-- TODO list -->
  <Todo />

  <!-- Send data betweend child and parent -->
  <ChildComp @response="(msg) => childMsg = msg", :msg="msg" >Message: {{ msg }}</ChildComp>

  <p> {{ childMsg }} </p>

  <UserInput />

</template>


<style>
.done {
  text-decoration: line-through;
}
</style>