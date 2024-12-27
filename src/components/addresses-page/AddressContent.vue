<script setup lang="ts">
import type { AddressType } from '@/types/addressType'
import AddressItem from './AddressItem.vue'
import axios from 'axios'
import { ref } from 'vue'
import LoadingSppinar from '@/shared/components/LoadingSppinar.vue'
import { toast } from 'vue3-toastify'

const addresses = ref<AddressType[]>([])
const loading = ref(false)

const getAddresses = async () => {
  loading.value = true
  const response = await axios.get('https://stage.achareh.ir/api/karfarmas/address', {
    headers: {
      'Content-Type': 'application/json',
      Authorization: 'Basic MDk4MjIyMjIyMjI6U2FuYTEyMzQ1Njc4',
    },
  })
  addresses.value = response.data
}

getAddresses()
  .catch(() => {
    toast.error('خطا در دریافت آدرس ها')
  })
  .finally(() => (loading.value = false))
</script>

<template>
  <main>
    <div class="title">آدرس ها و مشخصات</div>
    <AddressItem v-for="address in addresses" :key="address.id" :address="address" />
    <LoadingSppinar v-if="loading" />
  </main>
</template>
<style lang="scss" scoped>
main {
  padding: 16px;
  .title {
    color: #37474f;
    font-size: 16px;
    font-weight: 400;
  }
  @media screen and (min-width: 768px) {
    width: 768px;
    margin: 0 auto;
  }
}
</style>
