<template>
  <q-page class="q-pa-md">
    <h4>Popis svih knjiga</h4>

    <q-table
      title="Knjige"
      :rows="rows"
      :columns="columns"
      row-key="id"
      flat
      bordered
      dense
    />
  </q-page>
</template>

<script setup>
const columns = [
  { name: 'id', label: 'ID', field: 'id', align: 'left', sortable: true, style: { fontSize: '14px' }, headerStyle: { fontSize: '18px' } },
  { name: 'naslov', label: 'Naslov', field: 'naslov', align: 'left' },
  { name: 'autor', label: 'Autor', field: 'autor', align: 'left' },
  { name: 'opis', label: 'Opis', field: 'opis', align: 'left' },
  { name: 'slika', label: 'Slika', field: 'slika', align: 'left' },
  { name: 'status', label: 'Status', field: 'status', align: 'left' }
]

const rows = [
  { id: 1, naslov: 'Na Drini ćuprija', autor: 'Ivo Andrić', opis: 'Roman o mostu', slika: 'slika1.jpg', status: 'slobodna' },
  { id: 2, naslov: 'Prokleta avlija', autor: 'Ivo Andrić', opis: 'Zatvorska priča', slika: 'slika2.jpg', status: 'zauzeta' },
  { id: 3, naslov: 'Zločin i kazna', autor: 'Dostojevski', opis: 'Klasik realizma', slika: 'slika3.jpg', status: 'slobodna' }
]
</script>
