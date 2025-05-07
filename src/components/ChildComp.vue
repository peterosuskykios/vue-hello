<script setup>
const props = defineProps({
    msg: String
})

const emit = defineEmits(['response'])
emit('response', 'hello world from child')

</script>


<template>
    <h1>3. Child component</h1>
    <h2>{{ msg || 'No props passed' }}</h2>
    <slot>Fallback content</slot>

</template>