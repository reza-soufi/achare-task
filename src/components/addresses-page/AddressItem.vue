<script setup lang="ts">
import type { AddressType } from '@/types/addressType'
import AddressInfo from './AddressInfo.vue'
import { useMonitorSize } from '@/composables/monitor-sizes'

const props = defineProps<{ address: AddressType }>()

const sizes = useMonitorSize()
</script>

<template>
  <div class="content">
    <AddressInfo
      v-if="sizes.isMobile.value"
      title="نام و نام خانوادگی"
      :info="props.address.first_name + ' ' + props.address.last_name"
    />
    <AddressInfo v-if="!sizes.isMobile.value" title="نام " :info="props.address.first_name" />
    <AddressInfo
      v-if="!sizes.isMobile.value"
      title="  نام خانوادگی"
      :info="props.address.last_name"
    />
    <AddressInfo title="جنسیت" :info="props.address.gender" />
    <AddressInfo title="شماره تلفن همراه" :info="props.address.coordinate_mobile" />
    <AddressInfo title="شماره تلفن ثابت" :info="props.address.coordinate_phone_number" />
    <hr class="hr" />
    <div class="address_box">
      <div class="address_title">آدرس</div>
      <div class="address_info">{{ props.address.address }}</div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.content {
  background-color: white;
  border-radius: 4px;
  padding: 16px;
  margin-top: 8px;
  .address_title {
    color: #9b9b9b;
    font-size: 14px;
    font-weight: 400;
  }

  .address_info {
    color: #37474f;
    font-size: 14px;
    font-weight: 700;
  }

  @media screen and (min-width: 768px) {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;

    .hr {
      display: none;
    }

    .address_box {
      width: 33.33%;
    }
  }
}
</style>
