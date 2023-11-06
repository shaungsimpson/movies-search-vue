<script setup>
import { RouterView } from 'vue-router'
import TheHeader from './components/TheHeader.vue'
</script>

<template>
    <TheHeader />
    <div class="my-6">
        <RouterView />
    </div>
</template>

<style scoped></style>
