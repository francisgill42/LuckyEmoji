<template>
  <v-app style="background:purple;">
    <v-navigation-drawer
      v-model="drawer"
      color="purple"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list>
        <v-list-item
        
        class="white"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>mdi-chart-bubble</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="title" />
          </v-list-item-content>
        </v-list-item>

          <v-list-item
        
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon color="white">{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="white--text" v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
     class="purple"
     dark
    :clipped-left="clipped"
    fixed
    app
    >

      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-btn
        class="hidden-md-and-down"
        icon
        @click.stop="miniVariant = !miniVariant"
      >
        <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
      </v-btn>
      <v-btn
      class="hidden-md-and-down"
        icon
        @click.stop="clipped = !clipped"
      >
        <v-icon>mdi-application</v-icon>
      </v-btn>
     
      <v-toolbar-title class="ml-2" v-text="`user name`" />
      <v-spacer></v-spacer>
      <v-btn small text @click="logout">     
        <v-icon>mdi-logout</v-icon>
      </v-btn>
     </v-app-bar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer
    color="purple"
     class="white--text"
      :fixed="fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
      <v-spacer />
      <a class="white--text" style="text-decoration:none;"
      href ="mailto: francisgill1000@gmail.com/">Contact Us</a>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
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
          title: 'Redeem Coins',
          to: '/redeem_coins'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: ' Lucky Emoji'
    }
  },
  methods:{
    logout () {
      this.$auth.logout();
    }
  }
}
</script>
