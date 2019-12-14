<template>
  <v-container>
    <v-alert v-if="hasErrors" border="left" type="error">
      Hubo un error al solicitar la información.
    </v-alert>

    <APOD v-if="apod" :info="apod" />

    <v-layout justify-center text-center>
      <v-flex xs12 sm6 md4>
        <h4 class="display-1 mt5">
          Esta aplicación está construída por motivos educacionales y sin fines
          de lucro
        </h4>
      </v-flex>
    </v-layout>
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
