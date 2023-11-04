<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount, watch, nextTick } from 'vue';
import { useRoute } from 'vue-router';

const showElement = ref(false);
const route = useRoute();

const setNavbarVisibility = () => {
  showElement.value = route.path !== '/';
};

const handleScroll = () => {
  if (route.path === '/') {
    showElement.value = window.scrollY > (window.innerHeight * 0.8);
  }
};

watch(() => route.path, () => {
  setNavbarVisibility();
});

onMounted(() => {
  nextTick(() => {
    setNavbarVisibility();
    if (route.path === '/') {
      window.addEventListener('scroll', handleScroll);
      handleScroll();
    }
  });
});

onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>

<template>
  <div :class="{ 'slide-down': showElement, 'slide-up': !showElement }"
    class="w-full flex flex-col items-center bg-stone-100 text-stone-900 mb-4 transition-all ease-in-out duration-500">
    <div class="w-full my-2 px-6 md:px-14 flex justify-between text-lg">
      <NuxtLink id="branding" to="/" class="font-medium flex items-center">
        <div id="thetext" :class="{ 'text-slide-down': showElement, 'text-slide-up': !showElement }" class="transition-text spartan-medium tracking-wider">LIBRE PHOTOGRAPHY</div>
      </NuxtLink>
      <div class="space-x-6 font-medium">
        <NuxtLink to="/about" activeClassBAK="text-primary-light"
          class="border-b-2 transition-all border-stone-100 hover:border-stone-600 duration-100 text-sm md:text-base spartan-medium tracking-wider uppercase">About</NuxtLink>
        <NuxtLink to="/" activeClassBAK="text-primary-light"
          class="border-b-2 border-stone-100 hover:border-stone-600 transition-all duration-100 text-base spartan-medium tracking-wider uppercase hidden">Contact</NuxtLink>
      </div>
    </div>
  </div>
</template>

<style scoped>
.slide-down,
.logo-slide-down,
.text-slide-down {
  transform: translateY(0);
}

.slide-up,
.logo-slide-up,
.text-slide-up {
  transform: translateY(-100%);
}

.transition-all {
  transition: all 0.2s ease-in-out;
}

.transition-logo {
  transition: all 0.2s ease-in-out 0.2s; 
}

.transition-text {
  transition: all 0.2s ease-in-out 0.22s;}
</style>
 