<script setup lang="ts">
import CreateAddress from '@/components/home-page/createAddress.vue'
import { ref, provide } from 'vue'
import SuccessSubmiting from '@/components/home-page/SuccessSubmiting.vue'
const successSubmit = ref<boolean>(false)
provide('successSubmit', successSubmit)
</script>

<template>
  <main>
    <div v-if="!successSubmit">
      <div class="title">ثبت آدرس</div>
      <CreateAddress />
    </div>
    <div v-else>
      <SuccessSubmiting />
    </div>
  </main>
</template>

<style lang="scss" scoped>
main {
  padding: 16px 16px 100px;
  .title {
    color: #37474f;
    font-size: 16px;
    font-weight: 400;
  }
  @media screen and (min-width: 768px) {
    width: 808px;
    margin: 0 auto;
  }
}
</style>
