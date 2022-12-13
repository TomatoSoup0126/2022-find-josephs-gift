<template>
  <div
    class="mx-auto border rounded border-gray-300 w-8 h-8 flex items-center justify-center"
    :class="{'opacity-25': discard}"
  >
    {{ index }}
  </div>
</template>

<script setup>
import { defineProps } from 'vue'
const props = defineProps({
  index: {
    type: Number,
    required: true
  },
  discard: {
    type: Boolean,
    default: false
  }
})
</script>