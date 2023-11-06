<script setup>
import { ref } from 'vue';
import MovieResult from '../components/MovieResult.vue';

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
    <h1>Movies</h1>
    <div v-if="apiKey">
      <div>
        Search: <input type="text" v-model="search" />
        <button @click="search = ''">Clear</button>
        <button @click="searchMovies">Search</button>
      </div>
      <div>{{ totalResults }} results found.</div>
      <div>
        <MovieResult v-for="movie in movies" :key="movie.imdbID" :movie="movie" />
      </div>
    </div>
    <div v-else>
      <p>Please set the VITE_API_KEY environment variable.</p>
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
