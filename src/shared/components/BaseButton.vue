<template>
  <button
    :class="['btn', `btn--${type}`, `btn--${size}`]"
    :disabled="disabled"
    @click="handleClick"
  >
    <slot />
  </button>
</template>

<script lang="ts">
export default {
  name: 'ButtonComponent',
  props: {
    type: {
      type: String,
      default: 'primary', // Options: primary, secondary, success, danger, etc.
    },
    size: {
      type: String,
      default: 'medium', // Options: small, medium, large
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    handleClick(event: MouseEvent) {
      if (!this.disabled) {
        this.$emit('click', event)
      }
    },
  },
}
</script>

<style scoped>
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.5em 1em;
  font-size: 1rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition:
    background-color 0.3s,
    box-shadow 0.3s;
}

.btn--primary {
  background-color: #007bff;
  color: white;
}

.btn--primary:hover {
  background-color: #0056b3;
}

.btn--secondary {
  background-color: #6c757d;
  color: white;
}

.btn--secondary:hover {
  background-color: #5a6268;
}

.btn--success {
  background-color: #28a745;
  color: white;
}

.btn--success:hover {
  background-color: #218838;
}

.btn--danger {
  background-color: #dc3545;
  color: white;
}

.btn--danger:hover {
  background-color: #c82333;
}

.btn--small {
  font-size: 0.875rem;
  padding: 0.25em 0.5em;
}

.btn--medium {
  font-size: 1rem;
  padding: 0.5em 1em;
}

.btn--large {
  font-size: 1.25rem;
  padding: 0.75em 1.5em;
}

.btn:disabled {
  background-color: #d6d6d6;
  color: #8a8a8a;
  cursor: not-allowed;
}
</style>
