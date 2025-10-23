<template>
  <q-page padding>
    <!-- content -->

    <q-toolbar class="bg-grey-9 text-white">
      <q-toolbar-title>Nove knjige</q-toolbar-title>
    </q-toolbar>

      <div class="q-pa-md row items-start q-gutter-md">
       <q-card class="my-card">
        <img src="https://cdn.quasar.dev/img/mountains.jpg">

        <q-card-section>
          <div class="text-h6">Our Changing Planet</div>
          <div class="text-subtitle2">by John Doe</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          {{ lorem }}
        </q-card-section>
        </q-card>
        <q-card class="my-card">
        <img src="https://cdn.quasar.dev/img/mountains.jpg">

        <q-card-section>
          <div class="text-h6">Menza</div>
          <div class="text-subtitle2">Sranje</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          {{ menza }}
        </q-card-section>
        </q-card>

        <q-card class="my-card">
        <img src="https://cdn.quasar.dev/img/mountains.jpg">

        <q-card-section>
          <div class="text-h6">Rijeka koja teče</div>
          <div class="text-subtitle2">Grad od poplava</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          {{ rijeka }}
        </q-card-section>
        </q-card>

        <q-card class="my-card">
        <img src="https://cdn.quasar.dev/img/mountains.jpg">

        <q-card-section>
          <div class="text-h6">Our Changing Planet</div>
          <div class="text-subtitle2">by John Doe</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          {{ poirot }}
        </q-card-section>
        </q-card>
      </div>
  </q-page>
</template>

<script>
export default {
  setup () {
    return {
      lorem: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.',
      menza: 'Zašto u menzi nikad nema hrane, a kad ima hrane je gužva do wc-a',
      rijeka: 'Rijeka kišni grad. Nepomogne ti ni kišobran ni kabanica a bogami ni auto, uvijek završiš mokar',
      poirot: 'Poirot receives a visit from Miss Mary Marvell, the famous American film star on her visit to London. She has received three letters, handed to her by a Chinese man, which warn her to return her fabulous diamond jewel, the "Western Star"'
    }
  }
}
</script>

<style lang="sass" scoped>
.my-card
  width: 100%
  max-width: 250px
</style>
