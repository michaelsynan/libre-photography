<template>
  <MainHero />
  <div class="sticky-container">
    <ImageGallery :heading="'Street Photography'" class="sticky-gallery z-30" />
  </div>
  <div class="cover-gallery z-40">
    <ImageGallery :heading="'Weddings'" />
  </div>
  <div class="cover-gallery z-20">
    <ImageGallery :heading="'Concerts'" />
  </div>
  <ContactSection />
</template>

<style scoped>
.sticky-container {
  position: relative;
  z-index: 30;
  /* Margin to ensure sticky element doesn't overlap MainHero */
  margin-top: 100vh; 
}

.sticky-gallery {
  position: sticky;
  top: 0;
}

.cover-gallery {
  position: relative;
}
</style>
