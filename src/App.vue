<script setup>
import { ref } from 'vue'
import './style.css'
import SearchBar from './components/SearchBar.vue'
import ResultList from './components/ResultList.vue'

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


</script>

<template>
  <div class="container">

    
      <h1>Saras Search</h1>
      <SearchBar v-model="query" />
    

    <!-- ResultList component -->
    <ResultList :results="results" />
   
  </div>
</template>

