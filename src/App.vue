<script setup>
import Sidebar from '@/components/Sidebar.vue'
import { RouterView } from 'vue-router'
</script>

<template>
  <div class="grid grid-cols-6 min-h-screen p-6">
    <Sidebar class="col-span-1" />
    <RouterView class="col-span-5" />
  </div>
</template>
