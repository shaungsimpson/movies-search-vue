<script setup>
import { RouterLink } from 'vue-router'
defineProps({
    ...RouterLink.props,
    inactiveClass: String
})
const styles = {
    active: 'text-emerald-400 border-emerald-400 pointer-events-none',
    inactive: 'border-transparent text-emerald-600 hover:border-emerald-600 hover:text-emerald-600'
}
</script>

<template>
    <router-link v-bind="$props" custom v-slot="{ isActive, href, navigate }">
        <a
            v-bind="$attrs"
            :href="href"
            @click="navigate"
            class="flex items-center h-full px-4 py-2 font-semibold transition-all duration-300 ease-in border-b-4"
            :class="isActive ? styles.active : styles.inactive"
        >
            <slot />
        </a>
    </router-link>
</template>
