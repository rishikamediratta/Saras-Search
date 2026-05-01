<script setup>
import { ref, watch } from 'vue'
import './style.css'

import SearchBar from './components/SearchBar.vue'
import ResultList from './components/ResultList.vue'
import Loader from './components/Loader.vue'

// STATE
const query = ref('')
const results = ref([])
const loading = ref(false)
let latestQuery = ''

// API FUNCTION
async function fetchResults(q) {
  loading.value = true

  try {
    const res = await fetch(
      `https://en.wikipedia.org/w/api.php?action=query&list=search&srsearch=${q}&format=json&origin=*`
    )

    const data = await res.json()

   
    if (q !== latestQuery) return

    results.value = data.query.search.map((item, index) => {
      let cleanSnippet = item.snippet
        .replace(/<[^>]+>/g, "")
        .replace(/&amp;/g, "&")

      if (cleanSnippet.toLowerCase().startsWith(item.title.toLowerCase())) {
        cleanSnippet = cleanSnippet.slice(item.title.length).trim()
      }

      if (cleanSnippet.length > 150) {
        cleanSnippet = cleanSnippet.slice(0, 150) + "..."
      }

      return {
        id: item.pageid || index,
        title: item.title,
        snippet: cleanSnippet,
        expanded: false
      }
    })
  } catch (err) {
    console.error(err)
    results.value = []
  }

  loading.value = false
}

// DEBOUNCE + WATCH
let timeout = null

watch(query, (newVal) => {
  clearTimeout(timeout)

  const trimmed = newVal.trim()
  latestQuery = trimmed  

  if (!trimmed) {
    results.value = []
    loading.value = false
    return
  }

  timeout = setTimeout(() => {
    fetchResults(trimmed)
  }, 300)
})

// EXPAND HANDLER
function handleToggle(id) {
  results.value = results.value.map(item => ({
    ...item,
    expanded: item.id === id ? !item.expanded : false
  }))
}
</script>

<template>
  <div class="container">
    <h1>Saras Search</h1>

    <SearchBar v-model="query" />

    <Loader v-if="loading" />

    <ResultList 
      v-else-if="results.length > 0" 
      :results="results"
      @toggle="handleToggle"
    />

    <p v-else-if="query">No results found</p>
    <p v-else>Start typing to search...</p>
  </div>
</template>