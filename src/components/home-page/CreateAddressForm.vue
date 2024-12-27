<script setup lang="ts">
import type { AddressFormType } from '@/types/addressType'
import type { Ref } from 'vue'
import { inject } from 'vue'

const successSubmit = inject<Ref<boolean, boolean>>('successSubmit')
const addressValues = inject<Ref<AddressFormType>>('addressValues')

const validateMinLength = ({ value }: { value: string }) => {
  return value.length >= 3
}

const validateAddress = ({ value }: { value: string }) => {
  return value.length >= 10
}

const submitHandler = async (values: AddressFormType) => {
  if (addressValues) addressValues.value = values
  if (successSubmit) successSubmit.value = true
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
        :validation="[['required'], [validateMinLength as any]]"
        :validation-messages="{
          required: 'نام را وارد کنید',
          validateMinLength: 'نام باید حداقل ۳ کاراکتر باشد',
        }"
      />
    </div>
    <div class="input_container">
      <FormKit
        type="text"
        name="last_name"
        label="نام خانوادگی "
        placeholder="مثال: محمدی"
        :validation="[['required'], [validateMinLength as any]]"
        :validation-messages="{
          required: 'نام خانوادگی را وارد کنید',
          validateMinLength: 'نام خانوادگی باید حداقل ۳ کاراکتر باشد',
        }"
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
        :validation="[['required'], [validateAddress as any]]"
        :validation-messages="{
          required: 'آدرس را وارد کنید',
          validateAddress: 'آدرس باید حداقل ۱۰ کاراکتر باشد',
        }"
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
      <FormKit type="submit"> ثبت و ادامه </FormKit>
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
