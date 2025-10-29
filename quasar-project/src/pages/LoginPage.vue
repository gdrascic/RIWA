<template>
  <q-page class="q-pa-md">
    <h4>Prijava</h4>
    <q-input v-model="korime" label="Korisničko ime" outlined class="q-mb-md" />
    <q-input v-model="lozinka" label="Lozinka" type="password" outlined class="q-mb-md" />
    <q-btn color="primary" label="Potvrdi" @click="login" />
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
const korime = ref('')
const lozinka = ref('')

function login () {
  alert(`Prijavljen: ${korime.value}`)
}
</script>
