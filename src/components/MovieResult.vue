<script setup>
import { reactive, ref } from 'vue';
import BaseCard from './BaseCard.vue';

const props = defineProps({
    movie: {
        type: Object,
        required: true,
    }
})

const image = reactive({
    src: props.movie?.Poster == 'N/A' ? 'src/assets/image-not-available.png' : props.movie?.Poster ?? null,
    alt: props.movie?.Poster == 'N/A' ? "Image not available" : `${props.movie?.Title} poster`,
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
