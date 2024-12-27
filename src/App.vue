<script setup lang="ts">
import { RouterView } from 'vue-router'
import AppHeader from './shared/layout/AppHeader.vue'
</script>

<template>
  <ErrorBoundry>
    <AppHeader />
    <RouterView />
  </ErrorBoundry>
</template>
