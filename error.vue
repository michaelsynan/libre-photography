<script setup>
const error = useError();
</script>

<template>
    <NuxtLayout name="404">
        <div class="flex flex-col items-center justify-center text-center h-full">
            <div v-if="error.statusCode === 404">
                <h1 class="text-4xl">404</h1>
                <h2 class="text-xl">
                    {{ error.message }}
                </h2>
                <p class="mb-4">It looks like you found a glitch in the matrix...</p>
                <Btn msg="home" :icon="false" to="/" />
            </div>
        </div>
    </NuxtLayout>
</template>
