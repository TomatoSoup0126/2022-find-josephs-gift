<template>
  <main class="mt-16 container mx-auto">
    <h1 class="text-3xl text-center mb-4">Find Joseph's Gift</h1>
    <div class="flex items-center justify-center">
      <span class="mr-2">
        Pick a number from 2 to 30:
      </span>
      <input v-model="presentsNumber" type="range" min="2" max="30">
    </div>
    <p>step: {{ step }}</p>
    <div class="mx-auto mt-6">
      <ControlPanel
        :step="step"
        :discardPresents="discardPresents"
        @add="step += 1"
        @subtract="handleSubtract"
        @reset="step = 1"
        @forward="handleToLast"
      />
    </div>
    <div class="mx-auto grid gap-x-4 gap-y-4 grid-cols-5 place-content-center mt-6 max-w-xs">
      <PresentBox
        v-for="index in +presentsNumber"
        :key="index"
        :index="index"
        :discard="discardPresentsOnStep.includes(index)"
      />
    </div>
  </main>
</template>

<script setup>
import { ref, computed } from 'vue'
import PresentBox from './components/PresentBox.vue'
import ControlPanel from './components/ControlPanel.vue'

const presentsNumber = ref(10)
const step = ref(1)

const presents = computed(() => {
  return Array.from({ length: +presentsNumber.value }, (_, i) => i + 1)
})

const handleSubtract = () => {
  if (step.value > 1) {
    step.value -= 1
  }
}

const handleToLast = () => {
  step.value = discardPresents.value.length
}

const discardPresents = computed(() => {
  let array = [...presents.value]
  let currentStep = 0
  let offset = Math.round(array.length / 2)
  const result = []

  while (array.length > 1) {
    currentStep++
    const discardGift = array.splice(currentStep, 1)
    if (discardGift.length) {
      result.push(...discardGift)
    } else {
      if (currentStep - offset >= array.length) {
        offset = offset + Math.round(array.length / 2) + 1
        console.log('after:', offset)
      }
      const discardGift = array.splice(currentStep - offset, 1)
      result.push(...discardGift)
    }
  }
  return result
})

const discardPresentsOnStep = computed(() => {
  return discardPresents.value.slice(0, step.value)
})
</script>
