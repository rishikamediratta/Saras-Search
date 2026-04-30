<script setup>
const props = defineProps(['result'])

function toggle() {
  props.result.expanded = !props.result.expanded
}
</script>

<template>
  <div class="result-item" @click="toggle">
    <strong>{{ result.title }}</strong>

    <p v-if="result.expanded">
      {{ result.snippet }}
    </p>
  </div>
</template>