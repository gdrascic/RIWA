<template>
  <q-page class="q-pa-md">
    <h4>Pretraživanje knjiga</h4>

    <q-input v-model="pojam" label="Unesi pojam" outlined class="q-mb-md" />

    <div class="q-mb-md">
      <q-checkbox v-model="poAutor" label="Pretraži po autoru" />
      <q-checkbox v-model="poNaslovu" label="Pretraži po naslovu" />
    </div>

    <q-btn color="primary" label="Traži" @click="trazi" />

    <q-table
      v-if="rezultati.length"
      :rows="rezultati"
      :columns="columns"
      row-key="id"
      flat
      bordered
      dense
      class="q-mt-md"
    />
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const pojam = ref('')
const poAutor = ref(false)
const poNaslovu = ref(false)
const rezultati = ref([])

const columns = [
  { name: 'id', label: 'ID', field: 'id' },
  { name: 'naslov', label: 'Naslov', field: 'naslov' },
  { name: 'autor', label: 'Autor', field: 'autor' }
]

const sveKnjige = [
  { id: 1, naslov: 'Na Drini ćuprija', autor: 'Ivo Andrić' },
  { id: 2, naslov: 'Zločin i kazna', autor: 'Dostojevski' }
]

function trazi () {
  if (poAutor.value) {
    rezultati.value = sveKnjige.filter(k => k.autor.toLowerCase().includes(pojam.value.toLowerCase()))
  } else if (poNaslovu.value) {
    rezultati.value = sveKnjige.filter(k => k.naslov.toLowerCase().includes(pojam.value.toLowerCase()))
  } else {
    rezultati.value = []
  }
}
</script>
