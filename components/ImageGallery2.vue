<template>
    <div id="gallerywrapper">
      <teleport to="body">
    <!-- The background overlay appears immediately upon click -->
    <div v-if="selectedImage" class="fixed inset-0 bg-stone-950 bg-opacity-80 flex items-center justify-center">
      <!-- The container for the image and buttons, which will have the fade-in effect -->
      <div id="lightboxbg"
        :class="{'content-loaded': imageLoaded, 'opacity-0': !imageLoaded}"
        class="relative w-11/12 sm:w-full max-w-4xl mx-auto flex flex-col items-center transition-opacity duration-500">
        <!-- Your image, which when loaded will trigger the fade-in for the container -->
        <nuxt-img :src="selectedImage" id="lightboximg"
          class="block object-contain w-full max-w-full h-auto max-h-[80vh] mb-2 cursor-pointer"
          @click="closeLightbox" 
          @load="handleImageLoaded" />
        <!-- The buttons which are also included in the fade-in effect -->
        <div class="flex justify-center items-center gap-2">
          <a :href="selectedImage" download
            class="download-button bg-transparent text-stone-300 !bg-amber-700 hover:!bg-amber-600 py-1 px-2.5 text-sm z-50 flex items-center gap-2 tracking-wider shadow rounded-sm">
            <div class="pr-0.5">DOWNLOAD</div><i-mdi-download />
          </a>
          <button
            class="close-button bg-transparent text-stone-300 !bg-cyan-900 hover:!bg-cyan-800 py-1 px-2.5 text-sm z-50 flex items-center gap-2 tracking-wider shadow rounded-sm"
            @click="closeLightbox">
            <div class="pr-0.5">CLOSE</div><i-mdi-close />
          </button>
        </div>
      </div>
    </div>
  </teleport>

    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 px-2 md:px-10 py-0 bg-stone-100">
      <div
        class="m-2 sm:m-4 bg-cyan-950 flex justify-center items-center col-span-1 col-start-2 md:col-start-3 md:col-span-1 lg:col-start-4 lg:col-span-1 row-start-1">
        <h2
          class="spartan tracking-wider text-xl sm:text-3xl md:text-5xl font-bold bg-transparent uppercase text-center container mx-auto p-4 text-stone-100">
          {{ heading }}
        </h2>
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/17.webp'">
        <nuxt-img src="/17-small.webp" loading="lazy" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="17.webp" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/23.webp'">
        <nuxt-img src="/23-small.webp" loading="lazy" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="23.webp" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/24.webp'">
        <nuxt-img src="/24-small.webp" loading="lazy" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="24.webp" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/25.webp'">
        <nuxt-img src="/25-small.webp" loading="lazy" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="25.webp" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/27.webp'">
        <nuxt-img src="/27-small.webp" loading="lazy" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="27.webp" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/21.webp'">
        <nuxt-img src="/21-small.webp" loading="lazy" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="21.webp" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/28.webp'">
        <nuxt-img src="/28-small.webp" loading="lazy" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="28.webp" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '29.webp'">
        <nuxt-img src="/29-small.webp" loading="lazy" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="29.webp" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/30.webp'">
        <nuxt-img src="/30-small.webp" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="30.webp" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/test.jpg'">
        <nuxt-img src="/test.jpg" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="test.jpg" />
      </div>
      <div class="relative pb-[56.25%] m-2 sm:m-4" @click="selectedImage = '/test.jpg'">
        <nuxt-img src="/test.jpg" class="absolute inset-0 object-cover w-full h-full cursor-pointer" alt="test.jpg" />
      </div>
    </div>
  </div>
</template>


<script lang="ts" setup>
import { ref, watch, onMounted, onUnmounted } from 'vue';

const props = defineProps<{ heading?: string; }>();
const heading = ref(props.heading ?? 'Libre Photography');

const selectedImage = ref(null)
const imageLoaded = ref(false)

function handleImageLoaded() {
  imageLoaded.value = true;
}

watch(selectedImage, (newValue, oldValue) => {
  if (newValue) {
    // When a new image is selected, reset imageLoaded to false
    imageLoaded.value = false;
  }
  toggleBodyScroll(!!newValue);
});
function closeLightbox() {
  selectedImage.value = null
  imageLoaded.value = false // Reset the loaded state for next image
}

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
#lightboximg,
#lightboxbg {
  z-index: 1004 !important;
}

.sandwich {
  z-index: 1002 !important;

}

.z-1003 {
  z-index: 1003 !important;
}

/* Add CSS for the opacity animation */
/* Hide the content initially */
#lightboxbg.opacity-0 {
  opacity: 0;
}

/* Fade in the content quickly when the image is loaded */
.content-loaded {
  opacity: 1;
  transition: opacity 0.5s ease; /* Faster transition */
}

/* Ensure the background shows up immediately */
.fixed.bg-stone-950.bg-opacity-80 {
  transition: background-color 0.3s ease; /* Transition for background color if needed */
}
</style>