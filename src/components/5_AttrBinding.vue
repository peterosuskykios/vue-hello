<script setup>
import { ref } from 'vue';

const message = ref('THIS IS HINT')
const isRed = ref(true)
const color = ref('green')

function toggleRed() {
    isRed.value = !isRed.value
}

function toggleColor() {
    color.value = color.value === 'green' ? 'blue' : 'green'
}

</script>


<template>

    <h1>5. Attribute binding</h1>

    <p>
        <span :title="message">
            Hover mouse here to see HINT
        </span>
    </p>

    <p :class="{ red: isRed }" @click="toggleRed">Click to change to red and black</p>

    <p :style="{ color }" @click="toggleColor" >This will toggle between green and blue</p>

</template>


<style>
.red {
    color: red;
}

</style>