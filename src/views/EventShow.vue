<template>
  <h1>Showing event {{ event.title }}</h1>
</template>
<script>
import EventService from '@/services/EventService.js'

export default {
  props: ['id'],
  data() {
    return {
      event: {}
    }
  },
  created() {
    EventService.getEvent(this.id)
      .then(response => {
        //console.log('response.data = ', response.data)
        this.event = response.data
      })
      .catch(error => {
        console.log('There was an error', error.response) // If an error is returned log it to the console
      })
  }
}
</script>
