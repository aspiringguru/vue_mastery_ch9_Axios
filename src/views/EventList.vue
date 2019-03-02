<template>
  <div>
    <h1>Events Listing</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event"/>
  </div>
</template>

<script>
import EventCard from '@/components/EventCard.vue'
import EventService from '@/services/EventService.js'

export default {
  components: {
    EventCard
  },
  data() {
    return {
      events: []
    }
  },
  created() {
    //axios
    //.get('http://localhost:3000/events') // Call out to this URL
    EventService.getEvents()
      .then(response => {
        console.log('response.data = ', response.data)
        this.events = response.data
      })
      .catch(error => {
        console.log('There was an error', error.response) // If an error is returned log it to the console
      })
  }
}
</script>
