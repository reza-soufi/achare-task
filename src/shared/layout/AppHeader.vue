<script setup lang="ts">
import LOGO from '../../assets/images/achare.svg'
</script>

<template>
  <div class="app-header">
    <img :src="LOGO" alt="achare logo" />
    <div class="app-header__links">
      <RouterLink
        class="app-header__link"
        to="/"
        active-class="active-link"
        exact-active-class="exact-active-link"
      >
        ثبت آدرس
      </RouterLink>
      <RouterLink
        class="app-header__link"
        to="/addresses"
        active-class="active-link"
        exact-active-class="exact-active-link"
        >مشاهده آدرس‌ها</RouterLink
      >
    </div>
  </div>
</template>

<style scoped>
.app-header {
  height: 48px;
  background-color: #ffffff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 16px;
}

.app-header img {
  width: 45px;
  height: 25px;
}

.app-header__links {
  display: flex;
  gap: 16px;
  align-items: center;
}

.app-header__link {
  font-size: 12.5px;
  font-weight: bold;
  text-decoration: none;
  color: #00bfa5;
}
.active-link {
  color: #37474f;
  font-weight: bold;
}

.exact-active-link {
  color: #37474f;
}
</style>
