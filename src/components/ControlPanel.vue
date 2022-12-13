<template>
<div class="flex justify-center">
  <button @click="handleReset">
    <ForwardIcon class="mx-2 rotate-180 h-6 w-6 hover:text-blue-500 transition-colors" />
  </button>
  <button @click="handleSubtract">
    <PlayIcon class="mx-2 rotate-180 h-6 w-6 hover:text-blue-500 transition-colors" />
  </button>
  <button @click="handleAdd">
    <PlayIcon class="mx-2 h-6 w-6 hover:text-blue-500 transition-colors" />
  </button>
  <button @click="handleForward">
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
