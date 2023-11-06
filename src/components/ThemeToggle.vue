<script setup>
import { useDark, useToggle } from '@vueuse/core'
import { Switch } from '@headlessui/vue'
import { MoonIcon, SunIcon } from '@heroicons/vue/20/solid'
const isDark = useDark({
    selector: 'body',
    valueDark: 'dark',
    valueLight: 'light',
})
const toggleDark = useToggle(isDark)
</script>

<template>
    <Switch v-model="isDark" :class="isDark ? 'bg-emerald-700' : 'bg-emerald-500'" @click="toggleDark()"
        class="relative inline-flex w-8 h-5 transition-colors duration-200 ease-in-out border-2 border-transparent rounded-full cursor-pointer shrink-0 focus:outline-none focus-visible:ring-2 focus-visible:ring-white focus-visible:ring-opacity-75">
        <span class="sr-only">Use setting</span>
        <span aria-hidden="true"
            :class="isDark ? 'translate-x-3' : 'translate-x-0'"
            class="grid items-center w-4 h-4 transition duration-200 ease-in-out transform bg-white rounded-full ring-0">
            <SunIcon v-if="!isDark" class="w-4 h-4 mx-auto text-emerald-500" aria-hidden="true" />
            <MoonIcon v-if="isDark" class="w-3 h-3 mx-auto text-emerald-700" aria-hidden="true" />
        </span>
    </Switch>
</template>
