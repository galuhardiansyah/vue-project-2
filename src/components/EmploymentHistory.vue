<script setup>
import { ref } from 'vue';

const employmentsHistory = ref([])
</script>

<template>
 <div class="mt-5 mb-10">
    <h3 class="font-bold text-xl">Employment History</h3>
    <p class="mt-1 mb-5 text-sm text-gray-400">Show your relevant experience (last 10 years). Use bullet points to note your achievements. If possible - use numbers/facts (Achieved X, measured by Y, by doing Z)</p>
    <button class="text-blue-400 font-semibold text-sm">+ Add Employment</button>
 </div>
</template>
