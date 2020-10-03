<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-toolbar-title>Page title</v-toolbar-title>
      <v-spacer></v-spacer>
        <v-btn icon to="/about">
          <v-icon>mdi-magnify</v-icon>
        </v-btn>
        <v-btn icon to="/">
          <v-icon>mdi-heart</v-icon>
        </v-btn>
    </v-app-bar>
    <router-view>
    </router-view>
  </v-app>
</template>

<script>
export default {
  name: 'App'
}
</script>
