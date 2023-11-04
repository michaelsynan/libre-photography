<template>
  <div class="flex flex-col min-h-screen z-0 relative bg-custom">
    <MainNav id="thenav" class="z-50" />
    <div class="flex-grow relative z-10">
      <div class="z-20 relative">
        <slot />
      </div>
    </div>
    <MainFooter class="mt-auto z-20" />
  </div>
</template>

<style scoped>
#thenav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
}

.bg-custom {
  background-image: url('/hellsgate.webp');
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
}
</style>
