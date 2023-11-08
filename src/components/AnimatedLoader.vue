<script setup></script>

<template>
    <div class="flex items-center w-full h-full">
        <div class="relative inline-block w-20 h-20 mx-auto lds-ripple">
            <div class="absolute border-4 rounded-full opacity-100 border-sky-700 dark:border-white "></div>
            <div class="absolute border-4 rounded-full opacity-100 border-sky-700 dark:border-white "></div>
        </div>
    </div>
</template>

<style scoped>
/* .lds-ripple {} */
.lds-ripple div {
    animation: ripple-loader 2s cubic-bezier(0, 0.2, 0.8, 1) infinite;
}

.lds-ripple div:nth-child(2) {
    animation-delay: -1s;
}

@keyframes ripple-loader {
    0% {
        top: 36px;
        left: 36px;
        width: 0;
        height: 0;
        opacity: 0;
    }

    4.9% {
        top: 36px;
        left: 36px;
        width: 0;
        height: 0;
        opacity: 0;
    }

    5% {
        top: 36px;
        left: 36px;
        width: 0;
        height: 0;
        opacity: 1;
    }

    100% {
        top: 0px;
        left: 0px;
        width: 72px;
        height: 72px;
        opacity: 0;
    }
}
</style>
