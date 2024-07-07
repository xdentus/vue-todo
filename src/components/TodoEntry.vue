<script setup>
import { RouterLink } from 'vue-router'
const props = defineProps({
  task: Object,
})
</script>

<template>
  <div class="text-white">{{ task.title }}</div>
</template>
