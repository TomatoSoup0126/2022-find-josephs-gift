<template>
  <div class="mx-auto border rounded w-8 h-8 flex items-center justify-center">
    {{ index }}
  </div>
</template>

<script setup>
import { defineProps } from 'vue'
const props = defineProps({
  index: {
    type: Number,
    required: true
  }
})
</script>