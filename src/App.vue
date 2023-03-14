<script setup>
import { ref } from 'vue'

const purchasePrice = ref(0)
const downPayment = ref(0)
const repaymentTime = ref(0)
const interestRate = ref(0)
const loanAmount = ref(0)
const monthlyPayment = ref(0)

</script>

<template>
  <div class="flex">
    <label for="purchasePrice">Purchase Price</label> {{ purchasePrice }}
    <input  type="range" name="purchasePrice" min="0" max="1000000" step="50000" v-model="purchasePrice">
  </div>
</template>

