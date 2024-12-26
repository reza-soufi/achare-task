<template>
  <div class="container">
    <div class="loading"></div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}
.loading {
  border: 4px solid white;
  border-radius: 50%;
  border-top: 4px solid #3498db;
  width: 32px;
  height: 32px;
  animation: spin 2s linear infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
