<script setup>
import { computed, ref } from 'vue'
import MovieResult from '../components/MovieResult.vue'
import { MagnifyingGlassIcon } from '@heroicons/vue/20/solid'

const apiKey = import.meta.env.VITE_API_KEY
const search = ref('')
const movies = ref([])
const totalResults = ref(0)
const currentPage = ref(1)

const searchMovies = () => {
    const page = currentPage.value ? `&page=${currentPage.value}` : ''
    fetch(`http://www.omdbapi.com/?s=${search.value}&apikey=${apiKey}${page}`)
        .then((response) => response.json())
        .then((data) => {
            movies.value = data.Search
            totalResults.value = data.totalResults
        })
}
const fetchPage = (page) => {
    currentPage.value = page
    searchMovies()
}

const resultPages = computed(() => {
    return Math.ceil(totalResults.value / 10) ?? 1
})

</script>

<template>
    <main>
        <div class="inline-flex items-center justify-between w-full space-x-6">
            <h1>Movies</h1>
            <div class="w-full max-w-lg ml-auto lg:max-w-xs" v-if="apiKey">
                <label for="search" class="sr-only">Search</label>
                <div class="relative">
                    <div
                        class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none"
                    >
                        <MagnifyingGlassIcon class="w-5 h-5 text-gray-400 dark:text-emerald-200" aria-hidden="true" />
                    </div>
                    <input
                        id="search"
                        v-model="search"
                        name="search"
                        class="block w-full rounded-md  dark:placeholder:text-emerald-200 placeholder:text-gray-400 dark:bg-gray-700 py-1.5 pl-10 pr-3 dark:text-gray-300 focus:bg-white focus:text-gray-900 dark:focus:text-gray-300 focus:ring-emerald-700 sm:text-sm sm:leading-6 border-gray-300 border dark:border-gray-700"
                        placeholder="Search"
                        type="search"
                        @change="searchMovies"
                    />
                </div>
            </div>
            <div v-else>
                <p>Please set the VITE_API_KEY environment variable.</p>
            </div>
        </div>
        <div class="py-6 my-6">
            <p class="text-center"><span v-if="resultPages > 1">Page {{ currentPage }} of {{ resultPages }}</span> ({{ totalResults }} results found.)</p>
            <div class="grid grid-cols-5 gap-3 py-5">
                <MovieResult v-for="movie in movies" :key="movie.imdbID" :movie="movie" />
            </div>
        </div>
        <div class="flex justify-center space-x-2" v-if="resultPages > 1">
            <button
                class="px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md shadow-sm hover:bg-gray-50"
                :disabled="currentPage === 1"
                @click="fetchPage(currentPage - 1)"
            >Previous</button>
            <button
                class="px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md shadow-sm hover:bg-gray-50"
                :disabled="currentPage === resultPages"
                @click="fetchPage(currentPage + 1)"
            >Next</button>
        </div>
    </main>
</template>

<style>
@media (min-width: 1024px) {
    .about {
        min-height: 100vh;
        display: flex;
        align-items: center;
    }
}
</style>
