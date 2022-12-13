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
        :discard="!presentsDiscardByStep.includes(index)"
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

const presentsDiscardByStep = computed(() => {
  const array = [...presents.value]
  let stepTick = 0
  while (stepTick !== step.value) {
    stepTick += 1
    discardPresents(array, stepTick)
  }
  return array
})


const handleSubtract = () => {
  if (step.value > 1) {
    step.value -= 1
  }
}

const handleToLast = () => {
  console.log('handleToLast')
}

const discardPresents = (array, step) => {
  console.group('discardPresents', array, step)
  return array.splice(step > array.length ? Math.round(step / array.length) : step, 1)
}
</script>
