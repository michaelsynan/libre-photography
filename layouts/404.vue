<script lang="ts" setup></script>

<template>
  <div class="flex flex-col min-h-screen z-0 relative bg-stone-100 items-center justify-center text-stone-900">
    <MainNav />
    <div class="w-full flex-1 flex items-center justify-center p-4">
      <slot />
    </div>
  </div>
</template>


<style scoped></style>
