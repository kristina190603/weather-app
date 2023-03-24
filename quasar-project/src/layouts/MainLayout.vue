<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title>
          WEATHER APP
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>


    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">

</script>

<style setup>
.q-toolbar__title:first-child{ 
   display: flex !important; 
  justify-content: center;
  align-items: center;
  font-size: 2rem;
}
</style>
