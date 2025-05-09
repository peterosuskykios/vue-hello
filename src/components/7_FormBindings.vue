<script setup>
import { ref } from 'vue';

const text = ref('Type here')
const checked = ref(true)

</script>



<template>
    <h1>7. Form bindings</h1>

    <h2>Text input</h2>
    <input v-model="text">
    <p>{{ text }}</p>

    <h2>Checkbox</h2>
    <input type="checkbox" id="checkbox" v-model="checked">
    <label for="checkbox">Checkbox is {{ checked }}</label>


</template>