<template>
  <q-page class="q-pa-md">
    <h4>Registracija korisnika</h4>
    <q-form @submit="potvrdi">
      <q-input v-model="ime" label="Ime" outlined class="q-mb-md" />
      <q-input v-model="prezime" label="Prezime" outlined class="q-mb-md" />
      <q-input v-model="email" label="Email" outlined class="q-mb-md" />
      <q-input v-model="korime" label="Korisničko ime" outlined class="q-mb-md" />
      <q-input v-model="lozinka" label="Lozinka" type="password" outlined class="q-mb-md" />
      <q-btn color="primary" label="Potvrdi" type="submit" />
    </q-form>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
const ime = ref('')
const prezime = ref('')
const email = ref('')
const korime = ref('')
const lozinka = ref('')

function potvrdi () {
  alert(`Korisnik ${ime.value} ${prezime.value} registriran!`)
}
</script>
