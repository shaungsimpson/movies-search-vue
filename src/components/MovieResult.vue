<script setup>
defineProps(['movie'])
</script>

<template>
    <div class="h-full transition bg-gray-100 border border-gray-300 rounded-lg shadow dark:border-gray-950 dark:bg-slate-700 hover:scale-105">
        <div class="w-full h-64 rounded-t-lg">
            <img class="object-cover object-center w-full h-full rounded-t-lg" :src="movie.Poster == 'N/A' ? 'src/assets/image-not-available.png' : movie.Poster" alt="" />
        </div>
        <h3 class="px-3 py-4">{{ movie.Title }} ({{ movie.Year }})</h3>
    </div>
</template>

<style></style>
