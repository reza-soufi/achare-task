<script setup lang="ts">
import { onMounted, ref, inject } from 'vue'
import L from 'leaflet'
import type { AddressFormType } from '@/types/addressType'
import type { Ref } from 'vue'
import axios from 'axios'
import { toast } from 'vue3-toastify'

const lat = ref(0)
const lng = ref(0)
const map = ref()
const mapContainer = ref()
const loading = ref(false)

const addressValues = inject<Ref<AddressFormType>>('addressValues')
const showMap = inject<Ref<boolean, boolean>>('showMap')
const values = { ...addressValues?.value, lat: lat.value, lng: lng.value }

onMounted(() => {
  map.value = L.map(mapContainer.value).setView([51.505, -0.09], 13)
  L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
    attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
  }).addTo(map.value)
})

function getLocation() {
  if (navigator.geolocation) {
    navigator.geolocation.watchPosition((position) => {
      lat.value = position.coords.latitude
      lng.value = position.coords.longitude
      map.value.setView([lat.value, lng.value], 13)

      L.marker([lat.value, lng.value], { draggable: true })
        .addTo(map.value)
        .on('dragend', (event) => {
          lat.value = event.target._latlng.lat
          lng.value = event.target._latlng.lng
        })
    })
  }
}

getLocation()

const handleSubmit = async () => {
  loading.value = true
  await axios
    .post('https://stage.achareh.ir/api/karfarmas/address', values, {
      headers: {
        'Content-Type': 'application/json',
        Authorization: 'Basic MDk4MjIyMjIyMjI6U2FuYTEyMzQ1Njc4',
      },
    })
    .then(() => {
      if (showMap) showMap.value = true
    })
    .catch(() => {
      toast.error('خطا در ثبت آدرس')
    })
    .finally(() => (loading.value = false))
}
</script>

<template>
  <div ref="mapContainer" style="width: 100%; height: 500px"></div>
  <div class="submit-btn">
    <button class="location-btn" @click="handleSubmit" :disabled="loading">
      {{ loading ? 'لطفا صبر کنید' : 'ثبت و ادامه ' }}
    </button>
  </div>
</template>

<style scoped>
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
  .location-btn {
    width: 343px;
    height: 48px;
    background-color: #00bfa5;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 14px;
    font-weight: 700;
    cursor: pointer;
  }
}
</style>
