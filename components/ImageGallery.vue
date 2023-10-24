<template>
  <div>
    <h2 class="text-4xl font-bold bg-transparent pt-12 pb-8 uppercase text-left container mx-auto">{{ heading }}</h2>
    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4">
      <div v-for="n in 12" :key="n" class="relative pb-[56.25%]">
        <img src="test.jpg" class="absolute inset-0 object-cover w-full h-full" alt="Test Image" />
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';

const props = defineProps<{
  heading?: string;
}>();

const heading = ref(props.heading ?? 'Blick Photography');
</script>

<style scoped>
</style>
