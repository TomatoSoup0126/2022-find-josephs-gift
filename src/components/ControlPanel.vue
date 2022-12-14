<template>
<div class="flex justify-center">
  <button @click="handleReset" :disabled="step === 1" class="disabled:opacity-25">
    <ForwardIcon class="mx-2 rotate-180 h-6 w-6 hover:text-blue-500 transition-colors" />
  </button>
  <button @click="handleSubtract" :disabled="step === 1" class="disabled:opacity-25">
    <PlayIcon class="mx-2 rotate-180 h-6 w-6 hover:text-blue-500 transition-colors" />
  </button>
  <button @click="handleAdd" :disabled="step === discardPresents.length" class="disabled:opacity-25">
    <PlayIcon class="mx-2 h-6 w-6 hover:text-blue-500 transition-colors" />
  </button>
  <button @click="handleForward" :disabled="step === discardPresents.length" class="disabled:opacity-25">
    <ForwardIcon class="mx-2 h-6 w-6 hover:text-blue-500 transition-colors" />
  </button>
</div>
</template>

<script setup>
import { defineEmits, defineProps } from 'vue'
import { PlayIcon, ForwardIcon } from '@heroicons/vue/24/solid'

const props = defineProps({
  step: {
    type: Number,
    required: true
  },
  discardPresents: {
    type: Array,
    default: () => ([])
  }
})

const emit = defineEmits(['add', 'subtract', 'reset', 'forward'])

const handleAdd = () => {
  emit('add')
}

const handleSubtract = () => {
  emit('subtract')
}

const handleReset = () => {
  emit('reset')
}

const handleForward = () => {
  emit('forward')
}
</script>
