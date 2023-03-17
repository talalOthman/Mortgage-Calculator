<script setup>
defineProps(['result', 'title'])
</script>

<template>
    <div class="flex flex-col items-center p-5 md:p-0 font-mono md:gap-y-2">
        <p class="md:text-2xl">{{ title }}</p>
        <p class="md:text-4xl font-bold">{{ result.toLocaleString() }}$</p>
    </div>
</template>



