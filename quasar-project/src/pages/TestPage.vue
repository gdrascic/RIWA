<template>
  <q-page padding>
    <!-- content -->
     <h1>{{ poruka }}</h1>
     <p v-html="tijelo"></p>
     <p v-html="htmlText"></p>
     <p v-text="htmlText"></p>

     <p v-for="item in days" :key="item">
      <button v-if="item=='Ponedjeljak'">
        {{ item }}*
      </button>
      <button v-else-if="item=='Utorak'" v-show="false">
        {{ item }}
      </button>
      <button v-else>
        {{ item }}
      </button>
     </p>
     <q-input color="purple-12" v-model="text1" label="Item name" @keyup="log()"></q-input>
     <q-input color="green-3" v-model="text1" label="Item name" @keyup="log()"></q-input>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

  const poruka = "Test page"
  const tijelo = "Tekst na stranici"
  const htmlText ="<p><b>Formatirani tekst</b> na starnici</p>"
  const days = ['Ponedjeljak','Utorak','Srijeda','Četvrtak','Petak','Subota','Nedjelja']

  const text1 = ref('')
  text1.value = "Hello"
  function log() {
    console.log(text1.value)
    }
</script>
