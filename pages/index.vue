<template>
  <div class="relative">
    <!-- MainHero takes the full height of the viewport -->
    <MainHero class="fixed inset-0 MainHero" />

    <!-- Container for the galleries starts after the full viewport height -->
    <div id="imagegallerywrapper" class="sticky-container" style="margin-top: 100vh; z-index: 1000000 !important;">
      <ImageGallery id="imagegallery1" :heading="'Street'" class="sticky-gallery bg-stone-100 shadow-top" />
      <ImageGallery2 id="imagegallery2" :heading="'Nature'"
        class="sticky-gallery bg-stone-100 shadow-top" />
      <div class="h-20 bg-stone-100"></div>
    </div>
  </div>
</template>

<style scoped>
/* MainHero with lower z-index */
.MainHero {
  z-index: 0 !important;
}

/* Sticky container with higher z-index than MainHero */
.sticky-container {
  position: relative;
  z-index: 20 !important;
}

/* sticky-gallery elements with specific z-index, higher than MainHero */
.sticky-gallery {
  position: sticky;
  top: 0;
  z-index: 10 !important; /* This will be applied to both galleries */
}

#immagegallerywrapper {z-index: 10000 !important; /* Adjust if needed */}
/* If you need different z-index values for each gallery, you can assign them individually */
#imagegallery1 {
  z-index: 10000 !important; /* Adjust if needed */
}

#imagegallery2 {
  z-index: 10001 !important; /* Make sure this is higher than #imagegallery1 if they overlap */
}

/* Additional styles if needed */
</style>
