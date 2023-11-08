<template>
  <div id="theheadingwrapper" class="h-screen flex flex-col justify-center items-center w-full fixed  border-stone-100">
    <h1 ref="heading" id="theheading" class="text-stone-100 font-bold clamp-h1 opacity-0 animate-delay relative spartan-light tracking-widest">
      LIBRE PHOTOGRAPHY
    </h1>
    <div v-if="showArrow" class="absolute bottom-4 left-1/2 transform -translate-x-1/2 cursor-pointer" @click="scrollDown">
      <i-mdi-arrow-down class="text-3xl md:text-4xl animate-bounce animate-slowest" />
    </div>
  
  </div>
  <register class="z-100 hidden" />
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';

const heading = ref(null);
const showArrow = ref(true);

const scrollDown = () => {
  window.scrollTo({
    top: window.innerHeight,
    behavior: 'smooth',
  });
};

const handleScroll = () => {
  showArrow.value = window.scrollY < window.innerHeight * 0.2;
};

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

  window.addEventListener('scroll', handleScroll);
});

onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>

<style scoped>

/* #theheadingwrapper {
  border: 10px solid #f5f5f4;
  border-radius: 48px;
  box-shadow: 0 0 4px 40px #f5f5f4,
  0 0 0 -5px #f5f5f4; 
  overflow: hidden;
}

 
  /* Tailwind's 'sm' breakpoint is 640px by default 
  @media (max-width: 640px) {
    #theheadingwrapper {
      border: 6px solid #f5f5f4; 
/* Reduced border size for small screens 
    }


  }
*/


#theheading, #theheadingwrapper {
  z-index: 999 !important;
}
.clamp-h1 {
  font-size: clamp(2rem, 8vw, 7rem);
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
