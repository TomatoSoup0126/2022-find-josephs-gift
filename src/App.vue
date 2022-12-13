<template>
  <main class="mt-16 container mx-auto">
    <h1 class="text-3xl text-center mb-4">Find Joseph's Gift</h1>
    <div class="flex items-center justify-center">
      <span class="mr-2">
        Pick a number from 2 to 30:
      </span>
      <input v-model="presentsNumber" type="range" min="2" max="30">
    </div>
    <div class="mx-auto mt-6">
      <ControlPanel />
    </div>
    <div class="mx-auto grid gap-x-4 gap-y-4 grid-cols-5 place-content-center mt-6 max-w-xs">
      <PresentBox v-for="index in +presentsNumber" :key="index" :index="index" />
    </div>
  </main>
</template>

<script setup>
import { ref } from 'vue'
import PresentBox from './components/PresentBox.vue'
import ControlPanel from './components/ControlPanel.vue'

const presentsNumber = ref(30)
const step = ref(1)

</script>
