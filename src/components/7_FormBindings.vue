<script setup>
import { ref } from 'vue';

const text = ref('Type here')
const checked = ref(true)
const checkedNames = ref(['John'])
const checkedRadio = ref('One')

const select = ref('A')
const multiSelect = ref(['A'])


function checkboxChecked() {
    checkedNames.value.forEach(name => {
        console.log(name)
    })

}

</script>



<template>
    <h1>7. Form bindings</h1>

    <h2>Text input</h2>
    <input v-model="text">
    <p>{{ text }}</p>

    <h2>Checkbox</h2>
    <input type="checkbox" id="checkbox" v-model="checked">
    <label for="checkbox">Checkbox is: {{ checked }}</label>


    <h2>Multi checkbox</h2>
    <input type="checkbox" id="john" value="John" v-model="checkedNames" @click="checkboxChecked">
    <label for="john">John</label>
    <input type="checkbox" id="peter" value="Peter" v-model="checkedNames">
    <label for="peter">Peter</label>
    <input type="checkbox" id="martin" value="Martin" v-model="checkedNames">
    <label for="martin">Martin</label>

    <h2>Radio</h2>
    <input type="radio" id="one" value="One" v-model="checkedRadio">
    <label for="one">One</label>
    <input type="radio" id="two" value="Two" v-model="checkedRadio">
    <label for="two">Two</label>
    <p>Picked {{ checkedRadio }}</p>

    <h2>Select</h2>
    <select v-model="select">
        <option disabled>Please select one</option>
        <option>A</option>
        <option>B</option>
        <option>C</option>
    </select>
    <p>Selected {{ select }}</p>

    <h2>Multi Select</h2>
    <select v-model="multiSelect" multiple>
        <option disabled>You can select more options</option>
        <option>A</option>
        <option>B</option>
        <option>C</option>
    </select>
    <p>Selected {{ multiSelect }}</p>


</template>