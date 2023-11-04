<template>
  <div class="flex flex-col">
    <MainHero class="fixed inset-0 z-10" />

    <!-- Placeholder for MainHero -->
    <div id="placeholder" class="h-screen"></div>

    <!-- Galleries appear one after the other in normal document flow -->
    <!-- Position set to relative so z-index works -->
    <ImageGallery :heading="'Street'" class="gallery bg-stone-100 relative !z-20" style="z-index: 1000 !important;" />
    <ImageGallery2 :heading="'Nature'" class="gallery bg-stone-100 relative !z-20" style="z-index: 1000 !important;" />

    <!-- Space after galleries before footer or next content -->
    <!-- Position set to relative so z-index works -->
    <div class="h-20 bg-stone-100 relative z-20"></div>
  </div>
</template>

<style scoped>
/* Ensure the galleries take up the full width of their container */
.gallery {
  width: 100%;
}
</style>
