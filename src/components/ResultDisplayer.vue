<script setup>
defineProps(['result', 'title'])
</script>

<template>
    <div class="flex flex-col items-center p-5">
        <p>{{title}}</p>
        <p>{{ result.toLocaleString() }} $</p>
    </div>
</template>



