<script setup lang="ts">
import Check from '@/assets/images/Check.svg'
</script>

<template>
  <div class="success_container">
    <img :src="Check" alt="success" />
    <h2>اطلاعات شما با موفقیت ثبت شد</h2>
    <RouterLink
      class="success_link"
      to="/addresses"
      active-class="active-link"
      exact-active-class="exact-active-link"
    >
      مشاهده آدرس‌ها
    </RouterLink>
  </div>
</template>

<style scoped lang="scss">
.success_container {
  height: 50vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  h2 {
    color: #37474f;
    font-size: 14px;
    font-weight: 700;
  }
  .success_link {
    color: #00bfa5;
    font-size: 16px;
    font-weight: 700;
    margin-top: 10px;
    text-decoration: none;
    cursor: pointer;
    border: 1px solid #00bfa5;
    border-radius: 4px;
    padding: 5px 10px;
    width: 341px;
    height: 48px;
    display: flex;
    justify-content: center;
    align-items: center;
  }
}
</style>
