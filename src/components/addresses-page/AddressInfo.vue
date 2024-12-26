<script setup lang="ts">
const props = defineProps<{ title: string; info: string }>()
</script>

<template>
  <div class="container">
    <div class="title">{{ props.title }}</div>
    <div class="info">{{ props.info || '-' }}</div>
  </div>
</template>

<style scoped lang="scss">
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;

  .title {
    color: #9b9b9b;
    font-size: 14px;
    font-weight: 400;
  }

  .info {
    color: #37474f;
    font-size: 14px;
    font-weight: 700;
  }

  @media screen and (min-width: 768px) {
    display: block;
    width: 33.33%;
  }
}
</style>
