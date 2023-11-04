<template>
  <div class="flex flex-col justify-center min-h-screen aboutcontainer -mt-20">
    <div class="md:w-2/3 p-6 flex flex-col justify-center mx-auto text-left">
      <div id="aboutarea" ref="aboutArea" class="text-stone-900 max-w-3xl mx-auto">
        <h1 class="text-2xl font-bold opacity-0 animate-h1 tracking-wide">ABOUT LIBRE PHOTOGRAPHY</h1>
        <p class="tracking-wide text-base md:text-lg md-1.5 md:mt-3 !leading-loose opacity-0 animate-p">

          Welcome to Libre Photography — a curated collection of photographs that are dedicated to the public domain, 
          focused on New York City. These high-quality images encapsulate the city's dynamic landscapes and the vibrancy of urban life. 
          All photos on our site are <span><a href="https://creativecommons.org/public-domain/cc0/" class="border-b border-stone-900">CC0</a></span>
          licensed, meaning they are free for personal and commercial use with no attribution required. Enjoy unrestricted access to our photographic treasures.
        </p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

definePageMeta({
  layout: 'about'
})

const aboutArea = ref(null);

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries, observer) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          const children = entry.target.children;
          for (let i = 0; i < children.length; i++) {
            children[i].style.animationDelay = `${i * 0.2}s`;
            children[i].classList.add('animate-delay');
          }
          observer.unobserve(entry.target);
        }
      });
    },
    {
      threshold: 0.5
    }
  );

  if (aboutArea.value) {
    observer.observe(aboutArea.value);
  }
});
</script>

<style scoped>
/* ... other styles ... */

#aboutarea {
  transition: opacity 1s ease-in-out;
}

.animate-delay {
  animation: animate-fade-in-up 1.5s ease forwards;
}

@keyframes animate-fade-in-up {
  0% {
    opacity: 0;
    transform: translateY(20px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
