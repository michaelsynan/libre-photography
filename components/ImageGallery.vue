<template>
  <div>
    <teleport to="body">
  <div v-if="selectedImage" id="lightboxbg" class="fixed inset-0 bg-stone-950 bg-opacity-80 flex items-center justify-center">
    <div class="relative w-11/12 sm:w-full max-w-4xl mx-auto flex flex-col items-center">
      <img :src="selectedImage" id="lightboximg" class="block object-contain w-full max-w-full h-auto max-h-[80vh] mb-2" @click="selectedImage = null" />

      <div class="flex justify-center items-center gap-2">
        <a
          :href="selectedImage"
          download
          class="download-button bg-transparent text-stone-300 !bg-amber-700 hover:!bg-amber-600 transition ease-in-out duration-100 py-1 px-2.5 text-sm z-50 flex items-center gap-2 tracking-wider shadow rounded-sm"
        >
          <div class="pr-0.5 ">DOWNLOAD</div> <i-mdi-download />
        </a>
        <button
          class="close-button bg-transparent text-stone-300 !bg-cyan-900 hover:!bg-cyan-800 transition ease-in-out duration-100 py-1 px-2.5 text-sm z-50 flex items-center gap-2 tracking-wider shadow rounded-sm"
          @click="selectedImage = null"
        >
          <div class="pr-0.5 ">CLOSE</div><i-mdi-close />
        </button>
      </div>
    </div>
  </div>
</teleport>


    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 px-2 md:px-10 py-0 bg-stone-100">
      <div class="m-2 sm:m-4 bg-cyan-950 flex justify-center items-center">
        <h2 class="spartan tracking-wider text-xl sm:text-3xl md:text-5xl font-bold bg-transparent uppercase text-center container mx-auto p-4 text-stone-100">
          {{ heading }}
        </h2>
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/1.jpg'">
        <img src="/1.jpg" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="Image 1" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/2.jpg'">
        <img src="/2.jpg" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="Image 2" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/3.jpg'">
        <img src="/3.jpg" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="Image 3" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/4.jpg'">
        <img src="/4.jpg" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="Image 4" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/5.webp'">
        <img src="/5.webp" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="Image 5" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/15.webp'">
        <img src="/15.webp" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="Image 15" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/16.webp'">
        <img src="/16.webp" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="Image 16" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/18.webp'">
        <img src="/18.webp" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="Image 18" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/20.webp'">
        <img src="/20.webp" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="Image 20" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/21.webp'">
        <img src="/21.webp" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="Image 21" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/22.webp'">
        <img src="/22.webp" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="Image 22" />
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref, watch, onMounted, onUnmounted } from 'vue';

const props = defineProps<{ heading?: string; }>();
const heading = ref(props.heading ?? 'Blick Photography');
const selectedImage = ref(null);

const toggleBodyScroll = (shouldPreventScroll) => {
  const body = document.body;
  if (shouldPreventScroll) {
    body.classList.add('no-scroll');
  } else {
    body.classList.remove('no-scroll');
  }
};

watch(selectedImage, (newValue) => {
  toggleBodyScroll(!!newValue);
});

onMounted(() => {
  if (selectedImage.value) {
    toggleBodyScroll(true);
  }
});

onUnmounted(() => {
  toggleBodyScroll(false);
});
</script>


<style scoped>
</style>