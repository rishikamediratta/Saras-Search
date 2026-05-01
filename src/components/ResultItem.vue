<script setup>
defineProps(['result'])
const emit = defineEmits(['toggle'])
</script>

<template>
  <div class="result-item" @click="emit('toggle', result.id)">

    <!-- Title -->
    <strong>{{ result.title }}</strong>

    <!-- Snippet -->
    <p class="snippet">
      {{ result.snippet }}
    </p>

    <!-- Expand -->
    <transition name="fade">
      <p v-if="result.expanded" class="expanded">
        More details about "{{ result.title }}"
      </p>
    </transition>

  </div>
</template>