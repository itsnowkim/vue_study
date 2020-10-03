<template>
    <v-card height="150">
    <v-footer
      absolute
      :footer="footer"
      class="font-weight-medium"
    >
      <v-col
        class="text-center"
        cols="12"
      >
        {{ new Date().getFullYear() + ' ' + footer}} — <strong>Vuetify</strong>
      </v-col>
    </v-footer>
  </v-card>
</template>

<script>
export default {
  props: ['footer']
}
</script>
