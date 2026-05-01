<script setup>
import ResultItem from './ResultItem.vue'

defineProps(['results'])
const emit = defineEmits(['toggle'])
</script>

<template>
  <div>
    <ResultItem
      v-for="result in results"
      :key="result.id"
      :result="result"
      @toggle="emit('toggle', $event)"
    />
  </div>
</template>