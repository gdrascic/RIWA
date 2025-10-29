<template>
  <q-page class="q-pa-md">
    <h4>Nove knjige</h4>
    <q-card v-for="knjiga in noveKnjige" :key="knjiga.id" class="q-mb-md">
      <q-card-section>
        <div class="text-h6">{{ knjiga.naslov }}</div>
        <div class="text-subtitle2">{{ knjiga.autor }}</div>
        <div>{{ knjiga.opis }}</div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script setup>
const noveKnjige = [
  { id: 1, naslov: 'Harry Potter i Kamen mudraca', autor: 'J. K. Rowling', opis: 'Fantastična avantura' },
  { id: 2, naslov: 'Sjena vjetra', autor: 'Carlos Ruiz Zafón', opis: 'Misteriozni roman o knjigama' }
]
</script>
