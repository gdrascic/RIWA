<template>
  <q-page class="q-pa-md">
    <h4>Lokacija knjižnice</h4>
    <div id="map" style="height:500px;"></div>
  </q-page>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import * as L from 'leaflet'
import 'leaflet/dist/leaflet.css'

const initialMap = ref(null)

onMounted(() => {
  initialMap.value = L.map('map').setView([45.3312, 14.4322], 13)
  L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
    attribution: '&copy;<a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
  }).addTo(initialMap.value)
})
</script>
