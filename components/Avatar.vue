<template>
  <div class="rounded-full w-10 h-10 bg-gray-100 overflow-hidden">
    <img class="w-full h-full object-cover" :src="src" />
  </div>
</template>

<script setup>
const props = defineProps({
  src: {
    type: String,
    required: true,
  },
})
</script>
