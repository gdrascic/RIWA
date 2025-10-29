<template>
  <q-layout view="hHh lpR fFf">

    <q-header elevated>
      <q-toolbar>
        <q-btn flat dense round icon="menu" @click="leftDrawerOpen = !leftDrawerOpen" />
        <q-toolbar-title>Knjižnica</q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item clickable to="/">
          <q-item-section>Naslovnica</q-item-section>
        </q-item>
        <q-item clickable to="/noveknjige">
          <q-item-section>Nove knjige</q-item-section>
        </q-item>
        <q-item clickable to="/popisknjiga">
          <q-item-section>Popis svih knjiga</q-item-section>
        </q-item>
        <q-item clickable to="/pretrazivanje">
          <q-item-section>Pretraživanje</q-item-section>
        </q-item>
        <q-item clickable to="/lokacija">
          <q-item-section>Lokacija</q-item-section>
        </q-item>
        <q-item clickable to="/login">
          <q-item-section>Login</q-item-section>
        </q-item>
        <q-item clickable to="/registracija">
          <q-item-section>Registracija</q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
const leftDrawerOpen = ref(false)
</script>
