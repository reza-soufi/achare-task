<template>
  <slot v-if="!hasError" />
  <div v-else class="error-message">
    <p>An error occurred: {{ errorMessage }}</p>
    <button @click="resetError">تلاش دوباره</button>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      hasError: false,
      errorMessage: '',
    }
  },
  methods: {
    resetError() {
      this.hasError = false
      this.errorMessage = ''
    },
  },
  errorCaptured(err: unknown): boolean {
    this.hasError = true

    if (err instanceof Error) {
      this.errorMessage = err.message
    } else {
      this.errorMessage = 'Unknown error occurred'
    }

    return false
  },
}
</script>

<style scoped>
.error-message {
  color: red;
  text-align: center;
}
</style>
