<script lang="ts" setup>
import CreateAddressForm from '@/components/home-page/CreateAddressForm.vue'
</script>

<template>
  <div class="container">
    <p class="topic">لطفا مشخصات و آدرس خود را وارد کنید</p>
    <CreateAddressForm />
  </div>
</template>

<style lang="scss" scoped>
.container {
  height: 100%;
  background-color: white;
  border-radius: 4px;
  padding: 16px;
  margin-top: 14px;
  .topic {
    font-size: 12px;
    color: #37474f;
    font-weight: 700;
  }
  @media screen and (min-width: 768px) {
    padding: 22px 48px;
  }
}
</style>
