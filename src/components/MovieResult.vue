<script setup>
import { reactive, ref } from 'vue';
import BaseCard from './BaseCard.vue';

const props = defineProps(['movie'])
const image = reactive({
    src: props.movie?.Poster ?? 'src/assets/image-not-available.png',
    alt: props.movie?.Title ?? "Image not available",
})
const title = ref(`${props.movie?.Title} (${props.movie?.Year})` ?? null)
</script>

<template>
    <RouterLink :to="`/movies/${movie.imdbID}`">
        <BaseCard :image="image" :title="title" />
    </RouterLink>
</template>

<style>
</style>
