<script setup>
import { ref, watchEffect } from 'vue'

const API_URL = `https://api.github.com/repos/vuejs/core/commits?per_page=3&sha=`
const branches = ['main', 'minor']

const currentBranch = ref(branches[0])
const commits = ref([])

watchEffect(async () => {
  const url = `${API_URL}${currentBranch.value}`
  commits.value = await (await fetch(url)).json()
})

function truncate(v) {
    const newLine = v.indexOf('/n')
    return newLine > 0 ? v.slice(0, newLine) : v
}

function formatDate(v) {
    return v.replace(/T|Z/g, ' ')
}

</script>


<template>
    <h1>10. Fetch data</h1>
    <h2>Latest vure core commits</h2>

    <template v-for="branch in branches">
        <input type="radio"
        :id="branch"
        :value="branch"
        name="branch"
        v-model="currentBranch">
        <label :for="branch">{{ branch }}</label>
    </template>

    <p>vuejs/core@{{ currentBranch }}</p>

    <ul v-if="commits.length >0">
        <li v-for="{ html_url, sha, author, commit} in commits" :key="sha">
            <a :href="html_url" target="_blank" class="commit">{{ sha.slice(0, 7) }}</a>
            - <span>{{ truncate(commit.message) }}</span>
            by <span class="author"><a :href="author.html_url" target="_blank">{{ commit.author.name }}</a></span>
            at <span class="date">{{ formatDate(commit.author.date) }}</span>
        </li>
    </ul>


</template>


<style>
a {
text-decoration: none;
color: #42b883;
}
li {
line-height: 1.5em;
margin-bottom: 20px;
}
.author,
.date {
    font-weight: bold;
}
</style>