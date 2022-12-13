<template>
<div class="flex justify-center">
  <button>
    <ForwardIcon class="mx-2 rotate-180 h-6 w-6 hover:text-blue-500 transition-colors" />
  </button>
  <button>
    <PlayIcon class="mx-2 rotate-180 h-6 w-6 hover:text-blue-500 transition-colors" />
  </button>
  <button>
    <PlayIcon class="mx-2 h-6 w-6 hover:text-blue-500 transition-colors" />
  </button>
  <button>
    <ForwardIcon class="mx-2 h-6 w-6 hover:text-blue-500 transition-colors" />
  </button>
</div>
</template>

<script setup>
import { PlayIcon, ForwardIcon } from '@heroicons/vue/24/solid'
</script>
