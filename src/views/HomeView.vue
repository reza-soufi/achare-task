<script setup lang="ts">
import CreateAddress from '@/components/home-page/createAddress.vue'
</script>

<template>
  <main>
    <div class="title">ثبت آدرس</div>
    <CreateAddress />
  </main>
</template>

<style scoped>
main {
  padding: 16px;
}
.title {
  color: #37474f;
  font-size: 16px;
  font-weight: 400;
}
</style>
