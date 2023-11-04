<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>

<script setup lang="ts">
import '~/assets/css/main.css';

useHead({
  titleTemplate: (titleChunk) => {
    return titleChunk ? `${titleChunk} - LIBRE PHOTOGRAPHY` : 'LIBRE PHOTOGRAPHY';
  }
})
</script>
