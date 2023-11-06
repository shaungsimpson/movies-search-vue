<script setup>
import { ref } from 'vue';
import MovieResult from '../components/MovieResult.vue';
import { MagnifyingGlassIcon } from '@heroicons/vue/20/solid'

const apiKey = import.meta.env.VITE_API_KEY
const search = ref('')
const movies = ref([])
const totalResults = ref(0)


const searchMovies = () => {
  fetch(`http://www.omdbapi.com/?s=${search.value}&apikey=${apiKey}`)
    .then(response => response.json())
    .then((data) => {
      movies.value = data.Search
      totalResults.value = data.totalResults
    })
}
</script>

<template>
  <main>
    <div class="inline-flex items-center w-full space-x-6 justify-between">
      <h1 class="font-bold text-xl text-emerald-200">Movies</h1>
      <div class="w-full ml-auto max-w-lg lg:max-w-xs" v-if="apiKey">
        <label for="search" class="sr-only">Search</label>
        <div class="relative">
          <div class="pointer-events-none absolute inset-y-0 left-0 flex items-center pl-3">
            <MagnifyingGlassIcon class="h-5 w-5 text-emerald-200" aria-hidden="true" />
          </div>
          <input id="search" v-model="search" name="search"
            class="block w-full rounded-md border-0 placeholder:text-emerald-200 bg-gray-700 py-1.5 pl-10 pr-3 text-gray-300 placeholder:text-gray-400 focus:bg-white focus:text-gray-900 focus:ring-0 sm:text-sm sm:leading-6"
            placeholder="Search" type="search" @change="searchMovies" />
        </div>
      </div>
      <div v-else>
        <p>Please set the VITE_API_KEY environment variable.</p>
      </div>
    </div>
    <div class="py-6 my-6">
      <div class="text-center text-emerald-200">{{ totalResults }} results found.</div>
      <div class="grid grid-cols-5 gap-3 py-5">
        <MovieResult v-for="movie in movies" :key="movie.imdbID" :movie="movie" />
      </div>
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
