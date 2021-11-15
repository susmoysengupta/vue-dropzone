<template>
    <div @dragenter.prevent="toggle_active()" @dragleave.prevent="toggle_active()" @dragover.prevent @drop.prevent="drop" :class="{ 'bg-green-100 border-green-300 dark:bg-green-700': dragActive }" class="flex items-center justify-center w-full px-12 py-8 border-4 border-gray-300 border-dashed rounded dark:border-2">
        <div class="flex flex-col items-center justify-center gap-2 text-gray-500 dark:text-gray-100 ">
            <span>
                <svg xmlns="http://www.w3.org/2000/svg" :class="{ 'animate-bounce': droppedFile === null }" class="w-20 h-20" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 16a4 4 0 01-.88-7.903A5 5 0 1115.9 6L16 6a5 5 0 011 9.9M15 13l-3-3m0 0l-3 3m3-3v12" />
                </svg>
            </span>
            <p class="text-base md:text-xl font-semibold">Drag a file here</p>
            <p class="text-xs md:text-sm font-semibold dark:text-gray-400">Or if you prefer</p>
            <!-- File input -->
            <label for="file" class="p-2 text-xs md:text-sm font-semibold leading-tight text-gray-600 bg-purple-100 border rounded cursor-pointer dark:bg-purple-600 dark:border-none hover:bg-purple-200 dark:hover:bg-purple-700 hover:shadow-sm">
                <span class="text-purple-500 dark:text-gray-100">Select a file from your device</span>
                <input type="file" @change="selectedFile" name="file" id="file" class="hidden" />
            </label>
            <!-- Dropped file info -->
            <div v-if="droppedFile !== null" class="flex flex-wrap items-center justify-center gap-2 text-base font-semibold text-gray-600 dark:text-gray-100">
                <span class="text-xs md:text-sm">File: {{ droppedFile.name }}</span>
                <button @click="clearDropped()" class="inline-flex items-center justify-center">
                    <span>
                        <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 text-red-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2m7-2a9 9 0 11-18 0 9 9 0 0118 0z" />
                        </svg>
                    </span>
                </button>
            </div>
        </div>
    </div>
</template>
<script setup>
import useDropZone from '../services/dropZone.js';

const { dragActive, droppedFile, toggle_active, drop, clearDropped, selectedFile } = useDropZone();
</script>