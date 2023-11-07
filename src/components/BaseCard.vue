<script setup>
const props = defineProps({
    image: {
        type: Object,
        required: false,
    },
    title: {
        type: String,
        required: false,
    },
})
</script>

<template>
    <div
        class="h-full transition bg-gray-100 border border-gray-300 rounded-lg shadow dark:border-gray-950 dark:bg-slate-700 hover:scale-105">
        <div v-if="props.image.src" class="w-full h-64 rounded-t-lg">
            <img class="object-cover object-center w-full h-full rounded-t-lg"
                :src="props.image.src" :alt="props.image.alt" />
        </div>
        <h3 v-if="props.title" class="px-3 py-4">{{ props.title }}</h3>
        <slot></slot>

    </div>
</template>
