<template>
  <div class="h-screen relative">
    <MainHero class="fixed z-10" />
  </div>
  <div id="imagegallerywrapper" class="sticky-container absolute z-100">
    <ImageGallery id="imagegallery1" :heading="'Street'" class="sticky-gallery py-10 bg-stone-100 shadow-top z-100" />
    <ImageGallery2 id="imagegallery2" :heading="'Nature'"
      class="sticky-gallery pt-10 pb-2 bg-stone-100 shadow-top z-100" />
    <div class="h-20 bg-stone-100"></div>
  </div>
</template>

<style scoped>
#imagegallery1,
#imagegallery2,
#imagegallerywrapper,
#anotheritem {
  z-index: 1000 !important;
}

#anotheritem {
  z-index: 9;
}

.sticky-container {
  position: relative;
}

.sticky-gallery {
  position: sticky;
  top: 0;
}

.cover-gallery {
  position: relative;
}
</style>
