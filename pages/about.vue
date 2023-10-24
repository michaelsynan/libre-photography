<script lang="ts" setup>
useHead({
  title: 'About'
});
</script>

<template>
  <div class="h-screen flex flex-col md:flex-row">
    <img src="https://via.placeholder.com/150" alt="Profile Photo" class="md:w-1/3 object-cover" />
    <div class="md:w-2/3 p-4 flex flex-col justify-center">
      <div class="text-left">
        <h1 class="text-2xl font-bold">About Me</h1>
        <p class="text-lg mt-4">
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Labore, magnam.
        </p>
      </div>
    </div>
  </div>
</template>

<style scoped>
@media (max-width: 767px) {
  img {
    width: 100%;
  }
}
</style>
