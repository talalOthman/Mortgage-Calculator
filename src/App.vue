<script setup>
import { ref, computed } from 'vue'
import DataSlider from './components/DataSlider.vue'
const purchasePrice = ref(450000)
const downPayment = ref(135000)
const repaymentTime = ref(25)
const interestRate = ref(3)
const loanAmount = computed(() => purchasePrice.value - downPayment.value)
const monthlyPayment = computed(() => {
  const interest = interestRate.value / 100 / 12
  const payments = repaymentTime.value * 12
  const x = Math.pow(1 + interest, payments)
  const monthly = (loanAmount.value * x * interest) / (x - 1)
  return monthly.toFixed(0)
})

</script>

<template>
  <div class="flex flex-col items-center justify-center h-screen">
    <h1 class="text-3xl">Mortgage Calculator</h1>
    <div class="flex flex-col gap-y-3 p-3">
      <DataSlider type="Purchase Price" :min="0" :max="1000000" :step="50000" v-model="purchasePrice" symbol="$" />
      <DataSlider type="Down Payment" :min="0" :max="1000000" :step="50000" v-model="downPayment" symbol="$" />
      <DataSlider type="Repayment Time" :min="0" :max="30" :step="1" v-model="repaymentTime" symbol="years" />
      <DataSlider type="Interest Rate" :min="0" :max="10" :step="1" v-model="interestRate" symbol="%" />
    </div>
    <div class="flex gap-x-3">
      <div class="flex flex-col items-center p-5">
        <p>Loan Amount</p>
        <p>{{ loanAmount.toLocaleString() }} $</p>
      </div>
      <div class="flex flex-col items-center p-5">
        <p>Monthly Payment</p>
        <p>{{ monthlyPayment.toLocaleString() }} $</p>
      </div>
    </div>
  </div>
</template>



