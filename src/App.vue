<script setup>
import { ref, computed } from 'vue'
import DataSlider from './components/DataSlider.vue'
import ResultDisplayer from './components/ResultDisplayer.vue'
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
  <div class="flex flex-col items-center justify-center absolute inset-0 text-black bg-gray-300">
    <div class="flex flex-col items-center md:p-20 md:shadow-2xl">
    <h1 class="text-3xl md:text-5xl pb-10 font-bold font-mono">Mortgage Calculator</h1>
    <div class="flex flex-col p-5 md:p-10 gap-y-2 md:w-3/5">
      <div class="flex flex-col gap-y-2 md:gap-x-3 md:flex-row md:justify-around">
        <DataSlider type="Purchase Price" :min="0" :max="1000000" :step="50000"
          v-model="purchasePrice" symbol="$" />
        <DataSlider type="Down Payment" :min="0" :max="1000000" :step="50000" v-model="downPayment"
          symbol="$" />
      </div>
      <div class="flex flex-col gap-y-2 md:gap-x-3 md:flex-row md:justify-around">
        <DataSlider type="Repayment Time" :min="0" :max="30" :step="1" v-model="repaymentTime"
          symbol="years" />
        <DataSlider type="Interest Rate" :min="0" :max="10" :step="1" v-model="interestRate"
          symbol="%" />
      </div>
    </div>
    <div class="flex gap-x-3 md:gap-x-7  md:w-3/5 md:justify-evenly md:pt-2">
      <ResultDisplayer :result="loanAmount" title="Loan Amount" />
      <ResultDisplayer :result="monthlyPayment" title="Monthly Payment" />
    </div>
  </div>
  </div>
</template>










<!-- <template>
  <div class="flex flex-col items-center justify-center h-screen">
    <h1 class="text-3xl">Mortgage Calculator</h1>
    <div class="flex flex-col gap-y-3 p-5">
      <div class="md:flex md:gap-x-6">
        <DataSlider type="Purchase Price" :min="0" :max="1000000" :step="50000" v-model="purchasePrice" symbol="$" />
        <DataSlider type="Down Payment" :min="0" :max="1000000" :step="50000" v-model="downPayment" symbol="$" />
        <DataSlider type="Repayment Time" :min="0" :max="30" :step="1" v-model="repaymentTime" symbol="years" />
      </div>
      <div class="md:flex md:items-center md:justify-between">
        <DataSlider class="" type="Interest Rate" :min="0" :max="10" :step="1" v-model="interestRate" symbol="%" />
        <div class="flex gap-x-3 md:flex-grow md:justify-evenly">
          <ResultDisplayer :result="loanAmount" title="Loan Amount" />
          <ResultDisplayer :result="monthlyPayment" title="Monthly Payment" />
        </div>
      </div>
    </div>
  </div>
</template> -->



