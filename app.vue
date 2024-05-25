<script setup lang="ts">
import Header from './components/header.vue';

useHead({
  title: "Hatsuboshi Tools"
})
</script>

<template>
  <Header />
  <main class="p-8">
    <NuxtPage />
  </main>
</template>
