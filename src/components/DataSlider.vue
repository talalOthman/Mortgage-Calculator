<script setup>
import { defineProps, defineEmits } from 'vue'
defineProps(['modelValue', 'min', 'max', 'step', 'type', 'symbol'])
defineEmits(['update:modelValue'])


</script>

<template>
    <div class="flex flex-col md:p-4">
        <div class="flex gap-x-3 items-center justify-between font-mono md:pb-1">
            <label class="md:text-lg text-sm" :for="type">{{ type }}</label>
            <p class="md:text-2xl font-semibold">{{ modelValue.toLocaleString() }} {{symbol}} </p>
        </div>   
            <input class="md:w-80 accent-black"  type="range" :name="type" :min="min" :max="max" :step="step" :value="modelValue"
            @input="$emit('update:modelValue', $event.target.value.toLocaleString())">
    </div>
</template>




