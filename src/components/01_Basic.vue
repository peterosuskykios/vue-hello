<script setup>
import { ref, onMounted } from 'vue'

// reactive state
const count     = ref(0)
const rawHtml   = ref('<span style="color: red">This should be red.</span>')
const message   = ref('Hello world')
const text      = ref('')
const awesome   = ref(true)
const pElementRef = ref(null)

// functions that mutate state and trigger updates
function increment() {
  count.value++
  console.log('Count is ' + count.value)
}

function onInput(e) {
  text.value = e.target.value
}

function toggle() {
  awesome.value = !awesome.value
}

// lifecycle hooks
onMounted(() => {
  console.log(`The initial count is ${count.value}.`)
  pElementRef.value.textContent = 'hi'
})

</script>


<template>
    <h1>1. Basic</h1>
    <h2>{{ message.split('').reverse().join('') }}</h2>

    <button @click="increment">Count is: {{ count }}</button>
    <p>Using text interpolation: {{ rawHtml }}</p>
    <p>Using v-html directive: <span v-html="rawHtml"></span></p>

    <input :value="text" @input="onInput" placeholder="Type here">
    <p>{{ text }}</p>

    <button @click="toggle">How you feel about Vue</button>

    <h1 v-if="awesome">Vue is awesome</h1>
    <h1 v-else="awesome">Vue stinky</h1>

    <p ref="pElementRef">Hello</p>


</template>