<script lang="ts" setup>
// Your TypeScript logic here
</script>

<template>
  <div class="bg-gray-900 min-h-screen">
    <div class="flex flex-col items-center bg-custom">
      <MainNav class="fixed z-50" />
      <SideMenu class="fixed inset-y-0 z-50 hidden" />
      <div class="w-full">
        <slot />
        <MainFooter class="z-100" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.bg-custom {
  background-image: url('test.jpg');
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
}
</style>
