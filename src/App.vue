<script setup>
import { ref } from 'vue'
import './style.css'

const query = ref('')

const results = ref([
  {
    id: 1,
    title: "Vue basics",
    snippet: "Learn the fundamentals of Vue.js",
    expanded: false
  },
  {
    id: 2,
    title: "React basics",
    snippet: "Learn the fundamentals of React",
    expanded: false
  }
])

// toggle expand per item
function toggle(result) {
  result.expanded = !result.expanded
}
</script>

<template>
  <div class="container">

    <!-- Search Section -->
    <div class="search section">
      <h1>Saras Search</h1>
      <input 
        v-model="query" 
        type="text" 
        placeholder="Type your search" 
      />
    </div>

    <!-- Results Section -->
    <div class="result section">

      <!-- Empty state -->
      <p v-if="results.length === 0">No results found</p>

      <!-- Results list -->
      <div 
        v-for="result in results" 
        :key="result.id" 
        class="result-item"
        @click="toggle(result)"
      >
        <strong>{{ result.title }}</strong>

        <p v-if="result.expanded">
          {{ result.snippet }}
        </p>
      </div>

    </div>

  </div>
</template>

