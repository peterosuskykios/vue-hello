<script setup>
import { ref } from 'vue'

const message = ref('Reverse message')

function reverseMessage() {
    message.value = message.value.split('').reverse().join('')
}

</script>


<template>
    <h1>4. User input</h1>
    <p>{{ message }}</p>
    <button @click="reverseMessage">Reverse message</button>
    <button @click="message += '!' ">Insert ! to message</button>

</template>