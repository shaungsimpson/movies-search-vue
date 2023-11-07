<script setup>
import { onMounted, ref } from 'vue'
import { useRoute } from 'vue-router'
import WideSection from '../components/WideSection.vue';

const route = useRoute()
const apiKey = import.meta.env.VITE_API_KEY
const id = ref(route.params.id)
const movie = ref({})

onMounted(() => {

    fetch(`http://www.omdbapi.com/?i=${id.value}&apikey=${apiKey}&plot=full`)
        .then((response) => response.json())
        .then((data) => {
            movie.value = data
        })
})
</script>

<template>
    <main>
        <WideSection>

            <div class="grid gap-6 md:grid-cols-3 lg:grid-cols-12">
                <div class="lg:col-span-3">
                    <img class="object-cover aspect-[6/9] bg-slate-300 dark:bg-slate-700 max-w-fit-content"
                        :src="movie.Poster != 'N/A' ? movie.Poster : '/src/assets/image-not-available.png'"
                        alt="Movie Poster">
                </div>
                <dl class="md:col-span-2 lg:col-span-4">
                    <h1 class="text-2xl">{{ movie.Title ?? "Error, no title" }}</h1>
                    <p class="pb-6">{{ movie.Plot ?? "?" }}</p>
                    <h3>Actors</h3>
                    <p class="pb-6">{{ movie.Actors }}</p>
                    <h3>Ratings</h3>
                    <dl>
                        <span class="grid grid-cols-2" v-for="rating in movie.Ratings">
                            <dt>{{ rating.Source }}:</dt>
                            <dd class="text-right">{{ rating.Value }}</dd>
                        </span>
                    </dl>
                </dl>
                <div class="p-4 border rounded-lg shadow lg:col-span-2 bg-slate-100 dark:bg-slate-700 dark:border-slate-600">
                    <h3 class="text-lg text-center">Details</h3>
                    <dl class="grid grid-cols-2 text-sm gap-y-3">
                        <dt>Year:</dt>
                        <dd class="text-right">{{ movie.Year ?? "Error, no release date" }}</dd>
                        <dt>Rated:</dt>
                        <dd class="text-right">{{ movie.Rated ?? "?" }}</dd>
                        <dt>Released:</dt>
                        <dd class="text-right">{{ movie.Released ?? "?" }}</dd>
                        <dt>Runtime:</dt>
                        <dd class="text-right">{{ movie.Runtime ?? "?" }}</dd>
                        <dt>Genre(s):</dt>
                        <dd class="text-right">{{ movie.Genre ?? "?" }}</dd>
                        <dt>Language:</dt>
                        <dd class="text-right">{{ movie.Language ?? "?" }}</dd>
                    </dl>
                </div>
                <div class="p-4 border rounded-lg shadow md:col-span-2 lg:col-span-3 bg-slate-100 dark:bg-slate-700 dark:border-slate-600">
                    <h3 class="text-lg text-center">Production</h3>
                    <dl class="grid grid-cols-2 text-sm gap-y-3">
                        <dt>Director:</dt>
                        <dd class="text-right">{{ movie.Director ?? "?" }}</dd>
                        <dt>Writer:</dt>
                        <dd class="text-right">{{ movie.Writer ?? "?" }}</dd>
                        <dt>Country:</dt>
                        <dd class="text-right">{{ movie.Country ?? "?" }}</dd>
                        <dt>Awards:</dt>
                        <dd class="text-right">{{ movie.Awards ?? "?" }}</dd>
                        <dt>BoxOffice:</dt>
                        <dd class="text-right">{{ movie.BoxOffice ?? "?" }}</dd>
                    </dl>
                </div>
            </div>

        </WideSection>
    </main>
</template>

<style>
</style>
