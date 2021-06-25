<template>
  <v-app dark>
    <v-app-bar fixed app color="white" elevate-on-scroll>
      <v-img
        contain
        src="https://venturebeat.com/wp-content/uploads/2020/04/blue-prism-logo-landscape-image-oct-09-e1587418754694.jpg?w=1200&strip=all"
        max-height="100"
        max-width="200"
      >
      </v-img>
      <v-spacer></v-spacer>
      <v-btn class="mx-2" text> Home </v-btn>
      <v-btn class="mx-2" text> About us </v-btn>
      <v-btn class="mx-2" text> Contact Us </v-btn>
      <v-btn class="mx-2" text> FAQ </v-btn>
      <v-btn class="mx-2 px-10" rounded color="primary"> LOGIN </v-btn>
    </v-app-bar>

    <v-main>
      <nuxt />
    </v-main>

    <v-footer
      :absolute="!fixed"
      app
      style="background: #fafafb; height: 20vh"
      class="mt-10"
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>
