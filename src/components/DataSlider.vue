<script setup>
import { ref } from 'vue'
defineProps(['modelValue', 'min', 'max', 'step', 'type'])
defineEmits(['update:modelValue'])

</script>

<template>
    <div class="flex">
        <label :for="type">{{ type }}</label> {{ modelValue }}
        <input type="range" :name="type" :min="min" :max="max" :step="step" :value="modelValue"
            @input="$emit('update:modelValue', $event.target.value)">
    </div>
</template>

