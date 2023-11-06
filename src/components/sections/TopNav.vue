<script setup>
import TopNavLink from '../sections/TopNavLink.vue'
import { Disclosure, DisclosureButton, DisclosurePanel } from '@headlessui/vue'
import { Bars3Icon, XMarkIcon } from '@heroicons/vue/24/outline'
import ThemeToggle from '../ThemeToggle.vue'
</script>

<template>
    <Disclosure as="nav" class="h-16" v-slot="{ open }">
        <div class="max-w-full mx-auto">
            <div class="relative flex justify-between h-16">
                <div class="absolute inset-y-0 left-0 flex items-center sm:hidden">
                    <!-- Mobile menu button -->
                    <DisclosureButton
                        class="relative inline-flex items-center justify-center p-2 text-gray-400 rounded-md dark:text-gray-200 hover:bg-gray-100 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-emerald-500"
                    >
                        <span class="absolute -inset-0.5" />
                        <span class="sr-only">Open main menu</span>
                        <Bars3Icon v-if="!open" class="block w-4 h-4" aria-hidden="true" />
                        <XMarkIcon v-else class="block w-4 h-4" aria-hidden="true" />
                    </DisclosureButton>
                </div>
                <div
                    class="flex items-center justify-center flex-1 sm:items-stretch sm:justify-start"
                >
                    <nav class="hidden sm:flex">
                        <!-- Current: "border-emerald-500 text-gray-900 dark:text-gray-100", Default: "border-transparent text-emerald-500 hover:border-emerald-300 hover:text-gray-700 dark:hover:text-gray-200" -->
                        <TopNavLink to="/">Home</TopNavLink>
                        <TopNavLink to="/movies">Movies</TopNavLink>
                    </nav>
                </div>
                <div
                    class="absolute inset-y-0 flex items-center pr-2 right-12 sm:static sm:inset-auto sm:ml-6 sm:pr-0"
                >
                    <ThemeToggle />
                </div>
            </div>
        </div>

        <DisclosurePanel
            class="absolute z-20 w-full border-b-2 shadow-lg dark:bg-slate-700 bg-slate-100 sm:hidden border-b-emerald-500/50"
        >
            <nav class="p-1 space-y-1">
                <!-- Current: "bg-emerald-50 border-emerald-500 text-emerald-700", Default: "border-transparent text-emerald-500 hover:bg-emerald-50 hover:border-emerald-300 hover:text-gray-700 dark:hover:text-gray-200" -->
                <TopNavLink
                    to="/"
                    class="z-20 block hover:bg-emerald-50 hover:border-emerald-300 hover:text-gray-700 dark:hover:text-gray-200"
                    active-class="pl-4 text-emerald-500 border-emerald-500 bg-emerald-50 text-emerald-700"
                    inactive-class="border-transparent"
                >
                    Dashboard</TopNavLink
                >
                <TopNavLink
                    to="/movies"
                    class="z-20 block hover:bg-emerald-50 hover:border-emerald-300 hover:text-gray-700 dark:hover:text-gray-200"
                    active-class="pl-4 text-emerald-500 border-emerald-500 bg-emerald-50 text-emerald-700"
                    inactive-class="border-transparent"
                >
                    Movies</TopNavLink
                >
            </nav>
        </DisclosurePanel>
    </Disclosure>
</template>
