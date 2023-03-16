<script setup>
import { ref } from 'vue'
import DataSlider from './components/DataSlider.vue'
const purchasePrice = ref(500000)
const downPayment = ref(0)
const repaymentTime = ref(0)
const interestRate = ref(0)
const loanAmount = ref(0)
const monthlyPayment = ref(0)

</script>

<template>
  <DataSlider type="Purchase Price" :min="0" :max="1000000" :step="50000" v-model="purchasePrice" />
</template>

