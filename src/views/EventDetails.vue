<script setup>
import { ref, onMounted } from 'vue'

import EventService from '@/services/EventService.js'
const event = ref(null)
const props = defineProps({
  id: {
    required: true
  }
})

const getEventDetails = async () => {
  const res = await EventService.getEvent(props.id)
  console.log(res.data)
  event.value = res.data
}
onMounted(() => {
  getEventDetails()
})
</script>
<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }}@{{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>
<style></style>
