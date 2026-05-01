<template>
  <div class="loader">
    <div class="spinner"></div>
  </div>
</template>

<style scoped>
.loader {
  display: flex;
  justify-content: center;
  padding: 20px;
}

.spinner {
  width: 25px;
  height: 25px;
  border: 3px solid #ccc;
  border-top: 3px solid black;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  100% {
    transform: rotate(360deg);
  }
}
</style>