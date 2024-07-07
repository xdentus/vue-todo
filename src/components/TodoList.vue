<script setup>
import { reactive, onMounted } from 'vue'
import TodoEntry from '@/components/TodoEntry.vue'
import PulseLoader from 'vue-spinner/src/PulseLoader.vue'
import axios from 'axios'

const state = reactive({
  tasks: [],
  isLoading: true,
})

onMounted(async () => {
  try {
    const response = await axios.get('http://localhost:5000/tasks')
    state.tasks = response.data
    console.log(state.tasks)
  } catch (error) {
    console.error('Error fetching tasks', error)
  } finally {
    state.isLoading = false
  }
})
</script>

<template>
  <section>
    <div v-if="isLoading">
      <PulseLoader />
    </div>
    <div v-else class="flex flex-col">
      <TodoEntry v-for="task in state.tasks" :key="task.id" :task="task" />
    </div>
  </section>
</template>
