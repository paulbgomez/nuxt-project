<template>
   <div>
     <h1>Event {{ event.title }}</h1>
   </div>
</template>

<script>
export default {
      async asyncData({ $axios, error}) {
    try {
      const { data } = await $axios.get('http://localhost:3000/events' + params.id)
        return {
          data
        }
    } catch (e) {
      error({
        statusCode: 503,
        message: 'Unable to fetch #' + params.id + ' event at this time'
      })
    }
  },
    head() {
      return {
        title: 'Event #' + this.event.title,
        meta: [
          {
            hid: 'description',
            name: 'description',
            content: 'What you need to know about Event #' + this.event.title
          }
        ]
      }
    }
}
</script>