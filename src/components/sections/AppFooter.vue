<script setup>
const date = new Date().getFullYear()
</script>

<template>
    <footer
        class="bg-white border-t-2 dark:bg-slate-900 border-emerald-400/50 dark:border-emerald-700 dark:text-emerald-500 text-emerald-600 ">
        <div class="max-w-3xl px-4 mx-auto sm:px-6 lg:max-w-full lg:px-8">
            <div class="flex justify-between px-20 py-4 text-sm font-semibold">
                <div>
                    <h4 class="font-bold uppercase">Footer Menu</h4>
                    <ul class="font-semibold">
                        <li class="hover:underline hover:text-emerald-400">Footer Menu Item 1</li>
                        <li class="hover:underline hover:text-emerald-400">Footer Menu Item 2</li>
                        <li class="hover:underline hover:text-emerald-400">Footer Menu Item 3</li>
                        <li class="hover:underline hover:text-emerald-400">Footer Menu Item 4</li>
                    </ul>
                </div>
                <div>
                    <h4 class="font-bold uppercase">Footer Menu</h4>
                    <ul class="font-semibold">
                        <li class="hover:underline hover:text-emerald-400">Footer Menu Item 1</li>
                        <li class="hover:underline hover:text-emerald-400">Footer Menu Item 2</li>
                        <li class="hover:underline hover:text-emerald-400">Footer Menu Item 3</li>
                        <li class="hover:underline hover:text-emerald-400">Footer Menu Item 4</li>
                    </ul>
                </div>
                <div>
                    <h4 class="font-bold uppercase">Footer Menu</h4>
                    <ul class="font-semibold">
                        <li class="hover:underline hover:text-emerald-400">Footer Menu Item 1</li>
                        <li class="hover:underline hover:text-emerald-400">Footer Menu Item 2</li>
                        <li class="hover:underline hover:text-emerald-400">Footer Menu Item 3</li>
                        <li class="hover:underline hover:text-emerald-400">Footer Menu Item 4</li>
                    </ul>
                </div>
                <div class="h-full place-self-end">
                    <span class="block sm:inline">&copy; {{ date }} Your Company, Inc.</span> <span
                        class="block sm:inline">All
                        rights
                        reserved.</span>
                </div>
            </div>
        </div>
    </footer>
</template>
