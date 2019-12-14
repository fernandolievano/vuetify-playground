<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <h1 class="text-center display-3 my-5">Imagen del día</h1>
    </v-flex>
    <v-flex xs12 text-center>
      <v-img :lazy-src="info.url" :src="info.hdurl" class="my-2"></v-img>
      <h4 class="mb-2 title">{{ info.title }}</h4>
      <p class="body-1">
        {{ info.explanation }}
      </p>
      <p class="text-right font-italic">
        <v-chip color="secondary" small>
          {{ info.date }}
        </v-chip>
      </p>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  props: {
    info: {
      type: Object,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped></style>
