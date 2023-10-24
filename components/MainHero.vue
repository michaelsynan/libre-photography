<template>
  <div class="h-screen flex flex-col justify-center items-center bg-black bg-opacity-75 w-full fixed">
    <h1 ref="heading" class="text-white font-bold clamp-h1 opacity-0 animate-delay">
      BLICK PHOTOGRAPHY
    </h1>
  </div>
</template>



<script setup>
import { ref, onMounted } from 'vue';

const heading = ref(null);

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('animate-delay');
        }
      });
    },
    {
      threshold: 0.5,
    }
  );

  if (heading.value) {
    observer.observe(heading.value);
  }
});

</script>

<style scoped>
.clamp-h1 {
  font-size: clamp(2rem, 8vw, 6rem);
  line-height: 1.2;
  white-space: nowrap;
}

.animate-delay {
  animation-duration: 2s;
  animation-fill-mode: both;
  animation-name: animate-delay;
}

@keyframes animate-delay {
  0% {
    opacity: 0;
    transform: translateY(10px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
