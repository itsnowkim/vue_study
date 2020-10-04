<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <site-title :title="title"></site-title>
      <v-spacer></v-spacer>
        <v-btn icon to="/about">
          <v-icon>mdi-magnify</v-icon>
        </v-btn>
        <v-btn icon @click="save">
          <v-icon>mdi-check</v-icon>
        </v-btn>
        <v-btn icon @click="read">
          <v-icon>mdi-numeric</v-icon>
        </v-btn>

    </v-app-bar>
    <v-navigation-drawer app v-model="drawer">
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title">
            Application
          </v-list-item-title>
          <v-list-item-subtitle>
            subtext
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>
      <site-menu></site-menu>
    </v-navigation-drawer>
    <v-content>
      <router-view></router-view>
    </v-content>
    <site-footer :footer="footer"></site-footer>
  </v-app>
</template>

<script>
import SiteTitle from '@/views/site/title'
import SiteFooter from '@/views/site/footer'
import SiteMenu from '@/views/site/menu'

export default {
  components: { SiteTitle, SiteFooter, SiteMenu },
  name: 'App',
  data () {
    return {
      title: '나의 타이틀입니다',
      footer: 'footer입니다',
      right: null,
      drawer: false
    }
  },
  mounted () {
    console.log(this.$firebase)
  },
  methods: {
    save () {
      console.log('save@@@')
      this.$firebase.database().ref().child('abcd').set({
        title: 'abcd', text: 'ttttt'
      })
    },
    read () {
      this.$firebase.database().ref().child('abcd').on('value', (sn) => {
        console.log(sn)
        console.log(sn.val())
      })
    }
    // read는 변화에 계속 감지하는 리스너.
    // 한번만 read할 필요가 생기면 const로 변수에 넣어서 그 변수를 다루는 방식으로. async
  }
}
</script>
