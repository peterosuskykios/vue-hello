<script setup>
import Grid from './11.1_Grid.vue'
import { ref } from 'vue'

const searchQuery = ref('')
const gridColumns = ['name', 'power']
const gridData = [
    { name: 'Chuck Norris', power: 'infinity'},
    { name: 'Jackie Chan', power: 1000 },
    { name: 'Robo Facko', power: 2000 },
    { name: 'Chilli', power: 3000 },
]

</script>


<template>
    <h1>11. Grid with sort </h1>

    <form id="search">
        Search <input name="query" v-model="searchQuery">
    </form>

    <Grid
        :data="gridData"
        :columns="gridColumns"
        :filter-key="searchQuery">
    </Grid>

</template>
