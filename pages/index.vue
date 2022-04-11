<template>
  <h1>
    Events
  </h1>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
  async asyncData({ $axios, error}) {
    try {
      const { data } = await $axios.get('http://localhost:3000/events')
        return {
          data
        }
    } catch (e) {
      error({
        statusCode: 503,
        message: 'Unable to fetch events events at this time'
      })
    }
  },
  head() {
    return {
      title: 'Event Listing'
    }
  }
})
</script>
