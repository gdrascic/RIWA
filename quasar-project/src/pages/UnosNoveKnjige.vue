<template>
  <q-page padding class="bg-grey-2">
    <div class="text-center q-mb-xl">
      <div class="text-h4 text-primary text-weight-bold"> Dodavanje knjiga</div>
      <div class="text-subtitle2 text-grey-7">Unesite nove knjige u vašu kolekciju</div>
    </div>


    <q-card class="q-pa-lg q-mb-xl shadow-2 rounded-borders" style="max-width: 900px; margin: 0 auto;">
      <div class="row q-col-gutter-md">
        <q-input
          outlined
          v-model="novaKnjiga.naslov"
          label="Naslov knjige"
          class="col-12 col-md-6"
          lazy-rules
          :rules="[val => !!val || 'Naslov je obavezan']"
        />
        <q-input
          outlined
          v-model="novaKnjiga.autor"
          label="Autor"
          class="col-12 col-md-6"
          lazy-rules
          :rules="[val => !!val || 'Autor je obavezan']"
        />
        <q-input
          outlined
          v-model="novaKnjiga.opis"
          label="Opis knjige"
          type="textarea"
          class="col-12"
          placeholder="Kratki opis sadržaja knjige"
        />

        <div class="col-12 col-md-6">
          <q-file
            outlined
            v-model="novaKnjiga.slika"
            label="Odaberi naslovnicu"
            accept="image/*"
            use-chips
            clearable
            counter
          />
        </div>

        <div v-if="previewSlika" class="col-12 col-md-6 flex flex-center">
          <q-img
            :src="previewSlika"
            ratio="4/3"
            class="rounded-borders"
            style="max-height: 200px; width: 100%;"
          />
        </div>

        <q-select
          outlined
          v-model="novaKnjiga.status"
          :options="statusOpcije"
          label="Status knjige"
          class="col-12 col-md-6"
        />
      </div>

      <div class="row justify-end q-gutter-sm q-mt-lg">
        <q-btn
          color="secondary"
          flat
          icon="cancel"
          label="Odustani"
          @click="odustani"
        />
        <q-btn
          color="primary"
          icon="library_add"
          label="Spremi knjigu"
          @click="spremiKnjigu"
        />
      </div>
    </q-card>


    <div v-if="!knjige.length" class="text-center text-grey q-mt-xl">
      Trenutno nema unesenih knjiga.
    </div>

    <div v-else class="row q-col-gutter-lg q-mt-md">
      <q-card
        v-for="knjiga in knjige"
        :key="knjiga.id"
        bordered
        class="col-12 col-sm-6 col-md-4 q-pa-sm hover-card shadow-1"
      >
        <q-img
          v-if="knjiga.slikaUrl"
          :src="knjiga.slikaUrl"
          :alt="knjiga.naslov"
          style="height: 220px; object-fit: cover;"
        >
          <div class="absolute-bottom text-white text-center bg-primary q-pa-xs">
            {{ knjiga.naslov }}
          </div>
        </q-img>

        <q-card-section>
          <div class="text-subtitle1 text-weight-bold">{{ knjiga.autor }}</div>
          <div class="text-caption text-grey-7 q-mt-xs">{{ knjiga.opis }}</div>

          <div class="q-mt-sm">
            <q-badge
              :color="knjiga.status === 'Slobodna' ? 'positive' : 'negative'"
              class="text-weight-medium"
              align="top"
            >
              {{ knjiga.status }}
            </q-badge>
          </div>
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script setup>
import { ref, watch } from 'vue'

const statusOpcije = ['Slobodna', 'Zauzeta']

const novaKnjiga = ref({
  id: 0,
  naslov: '',
  autor: '',
  opis: '',
  slika: null,
  status: ''
})

const knjige = ref([])
const previewSlika = ref(null)

watch(() => novaKnjiga.value.slika, (nova) => {
  if (!nova) {
    previewSlika.value = null
    return
  }

  const file = Array.isArray(nova) ? nova[0] : nova
  if (file instanceof File) {
    previewSlika.value = URL.createObjectURL(file)
  }
})

function spremiKnjigu() {
  if (!novaKnjiga.value.naslov || !novaKnjiga.value.autor) {
    alert('Molimo unesite naslov i autora.')
    return
  }

  const noviId = knjige.value.length + 1

  const file = Array.isArray(novaKnjiga.value.slika)
    ? novaKnjiga.value.slika[0]
    : novaKnjiga.value.slika

  let slikaUrl = ''
  if (file instanceof File) {
    slikaUrl = URL.createObjectURL(file)
  }

  knjige.value.push({
    id: noviId,
    naslov: novaKnjiga.value.naslov.trim(),
    autor: novaKnjiga.value.autor.trim(),
    opis: novaKnjiga.value.opis.trim(),
    slikaUrl,
    status: novaKnjiga.value.status || 'Slobodna'
  })

  odustani()
}

function odustani() {
  novaKnjiga.value = {
    id: 0,
    naslov: '',
    autor: '',
    opis: '',
    slika: null,
    status: ''
  }
  previewSlika.value = null
}
</script>


