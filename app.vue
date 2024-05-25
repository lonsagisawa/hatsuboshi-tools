<script setup lang="ts">
import Header from './components/header.vue';
import '@fontsource/ibm-plex-sans-jp/100.css';
import '@fontsource/ibm-plex-sans-jp/200.css';
import '@fontsource/ibm-plex-sans-jp/300.css';
import '@fontsource/ibm-plex-sans-jp/400.css';
import '@fontsource/ibm-plex-sans-jp/500.css';
import '@fontsource/ibm-plex-sans-jp/600.css';
import '@fontsource/ibm-plex-sans-jp/700.css';

useHead({
  title: "Hatsuboshi Tools"
})
</script>

<template>
  <div class="max-w-2xl mx-auto">
    <Header />
    <main class="p-8">
      <NuxtPage />
    </main>
  </div>
</template>
