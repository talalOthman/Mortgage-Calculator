<script setup>
import { defineProps, defineEmits } from 'vue'
defineProps(['modelValue', 'min', 'max', 'step', 'type', 'symbol'])
defineEmits(['update:modelValue'])

</script>

<template>
    <div class="flex flex-col">
        <div class="flex gap-x-3">
            <label :for="type">{{ type }}:</label>
            <p>{{ modelValue.toLocaleString() }} {{symbol}} </p>
        </div>
        <input type="range" :name="type" :min="min" :max="max" :step="step" :value="modelValue"
            @input="$emit('update:modelValue', $event.target.value.toLocaleString())">
    </div>
</template>



