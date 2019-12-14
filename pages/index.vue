<template>
  <v-container>
    <v-alert v-if="hasErrors" border="left" type="error">
      Hubo un error al solicitar la información.
    </v-alert>

    <APOD v-if="apod" :info="apod" />
  </v-container>
</template>

<script>
import APOD from '@/components/home/APOD'

export default {
  components: {
    APOD
  },
  async asyncData({ $axios }) {
    try {
      const res = await $axios.$get(
        `planetary/apod?api_key=${process.env.NASA_API_KEY}`
      )

      return {
        apod: res,
        hasErrors: false
      }
    } catch (error) {
      return {
        apod: null,
        hasErrors: true
      }
    }
  }
}
</script>
