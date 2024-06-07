<script setup>
import { ref, onMounted } from 'vue'
import EventService from '@/services/EventService.js'
import EventCard from '@/components/EventCard.vue'
const events = ref(null)
const fetchData = async () => {
  const res = await EventService.getEvents()
  events.value = res.data
}
onMounted(() => {
  fetchData()
})
</script>

<template>
  <main>
    <h1>Good Events</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </main>
</template>
