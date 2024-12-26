<script setup lang="ts">
import type { AddressFormType } from '@/types/addressType'
import axios from 'axios'
import type { Ref } from 'vue'
import { inject, ref } from 'vue'

const loading = ref(false)

const successSubmit = inject<Ref<boolean, boolean>>('successSubmit')

const submitHandler = async (values: AddressFormType) => {
  loading.value = true
  await axios
    .post('https://stage.achareh.ir/api/karfarmas/address', values, {
      headers: {
        'Content-Type': 'application/json',
        Authorization: 'Basic MDk4MjIyMjIyMjI6U2FuYTEyMzQ1Njc4',
      },
    })
    .then(() => {
      if (successSubmit) successSubmit.value = true
    })
    .finally(() => (loading.value = false))
}
</script>

<template>
  <FormKit type="form" @submit="submitHandler">
    <div class="input_container">
      <FormKit
        type="text"
        name="first_name"
        label="نام"
        placeholder="مثال: علی"
        validation="required"
        :validation-messages="{ required: 'نام را وارد کنید' }"
      />
    </div>
    <div class="input_container">
      <FormKit
        type="text"
        name="last_name"
        label="نام خانوادگی "
        placeholder="مثال: محمدی"
        validation="required"
        :validation-messages="{ required: 'نام خانوادگی را وارد کنید' }"
      />
    </div>
    <div class="input_container">
      <FormKit
        type="text"
        name="coordinate_mobile"
        label="شماره تلفن همراه"
        placeholder="مثال: 09035896569"
        validation="required"
        :validation-messages="{ required: 'شماره تلفن همراه را وارد کنید' }"
      />
    </div>
    <div class="input_container">
      <FormKit
        type="text"
        name="coordinate_phone_number"
        label="شماره تلفن ثابت (اختیاری)"
        placeholder="مثال: 02145898765"
      />
    </div>
    <div class="input_container address_input">
      <FormKit
        type="text"
        name="address"
        label="آدرس"
        validation="required"
        :validation-messages="{ required: 'آدرس را وارد کنید' }"
      />
    </div>
    <div class="gender">
      <label for="gender"> جنسیت </label>
      <FormKit
        type="radio"
        id="gender"
        name="gender"
        :options="[
          { label: 'آقا', value: 'male' },
          { label: 'خانم', value: 'female' },
        ]"
      />
    </div>
    <div class="submit-btn">
      <FormKit
        type="submit"
        style="
          width: 343px;
          height: 48px;
          background-color: #00bfa5;
          color: white;
          border: none;
          border-radius: 4px;
          font-size: 14px;
          font-weight: 700;
        "
        :disabled="loading"
      >
        ثبت و ادامه
      </FormKit>
    </div>
  </FormKit>
</template>

<style scoped lang="scss">
.submit-btn {
  position: fixed;
  bottom: 0;
  right: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: white;
  box-shadow: 0 -2px 4px rgba(0, 0, 0, 0.1);
  height: 80px;
}
.gender {
  display: flex;
  align-items: center;
  margin-top: 26px;
  label {
    margin-left: 20px;
    font-size: 12px;
    color: #37474f;
    font-weight: 500;
  }
}
</style>
