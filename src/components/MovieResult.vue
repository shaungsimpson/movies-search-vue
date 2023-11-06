<script setup>
defineProps(['movie'])
</script>

<template>
    <div>
        <div>
            <h3>{{ movie.Title }}({{ movie.Year }})</h3>
            <img :src="movie.Poster" alt="">
        </div>
    </div>
</template>

<style></style>
