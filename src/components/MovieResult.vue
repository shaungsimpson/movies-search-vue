<script setup>
defineProps(['movie'])
</script>

<template>
    <div class="rounded-lg shadow border h-full border-gray-300 dark:border-gray-950 bg-gray-100 dark:bg-slate-700 transition hover:scale-105">
        <div class="w-full h-64 rounded-t-lg">
            <img class="w-full h-full object-cover object-center rounded-t-lg" :src="movie.Poster" alt="" />
        </div>
        <h3 class="px-3 py-4">{{ movie.Title }} ({{ movie.Year }})</h3>
    </div>
</template>

<style></style>
