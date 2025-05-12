<script setup>
import { ref } from 'vue';

const show = ref(true)
const list = ref([1, 2, 3])

</script>


<template>

    <h1>6. Conditionals loops</h1>

    <button @click="show = !show">Toggle number</button>
    <button @click="list.push(list.length + 1)">Push number</button>
    <button @click="list.pop()">Pop number</button>
    <button @click="list.reverse()">Reverse number</button>


    <ul v-if="show && list.length">
        <li v-for="item of list">{{ item }}</li>
    </ul>
    <p v-else-if="list.length">List is not empty, but hidden</p>
    <p v-else>List is empty</p>

</template>


