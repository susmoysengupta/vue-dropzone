<template>
    <div class="bg-gray-50 w-full min-h-screen flex items-center justify-center dark:bg-gray-900">
        <div class="flex flex-col items-center justify-center">
            <img alt="Vue logo" src="./assets/logo.png" class="w-32"/>
            <p class="text-3xl font-semibold text-gray-800 dark:text-gray-100 mb-8">Vue 3 Drop Zone</p>
            <drop-zone></drop-zone>
        </div>
    </div>
</template>

<script setup>
import DropZone from './components/DropZone.vue'
</script>