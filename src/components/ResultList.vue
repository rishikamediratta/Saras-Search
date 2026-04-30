<script setup>
import ResultItem from './ResultItem.vue'

defineProps(['results'])
</script>

<template>
  <div class="result section">
    
    <p v-if="results.length === 0">No results found</p>

    <ResultItem
      v-for="result in results"
      :key="result.id"
      :result="result"
    />
    
  </div>
</template>