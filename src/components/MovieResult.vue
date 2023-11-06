<script setup>
defineProps(['movie'])
</script>

<template>
    <div class="rounded border h-full bg-neutral-600">
        <img class="rounded-t" :src="movie.Poster" alt="">
        <h3 class="text-emerald-500 font-bold p-2">{{ movie.Title }} ({{ movie.Year }})</h3>
    </div>
</template>

<style>
</style>
