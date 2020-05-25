<template>
  <v-app dark>
    <v-app-bar
      color="primary"
      :clipped-left="$vuetify.breakpoint.lgAndUp"
      clipped-right
      app
    >
      <v-app-bar-nav-icon @click.stop="toggleDrawer" />
      <v-toolbar-title
        style="width: 300px"
        class="ml-0 pl-4"
        @click="$router.push('/')"
      >
        <span class="hidden-sm-and-down">{{ title }}</span>
      </v-toolbar-title>
      <v-spacer />
      <v-menu
        offset-y
        transition="scroll-y-transition"
        :close-on-click="true"
        :close-on-content-click="true"
      >
        <template v-slot:activator="{ on }">
          <v-btn icon large class="mr-1" v-on="on">
            <v-avatar size="38px" item>
              <v-icon dark x-large>mdi-account-circle</v-icon>
            </v-avatar>
          </v-btn>
        </template>
        <v-list dense>
          <v-list-item
            v-for="(item, index) in avatarMenuItems"
            :key="index"
            @click="avatarMenuItemClick(item.href)"
          >
            <v-list-item-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>
                {{ item.text }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>
    <v-navigation-drawer
      v-model="drawer"
      :clipped="$vuetify.breakpoint.lgAndUp"
      app
    >
    </v-navigation-drawer>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer app>
      <span>&copy; {{ new Date().getFullYear() }} {{ author }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: null,
      title: 'GDrive Manager',
      avatarMenuItems: [
        { icon: 'mdi-logout', text: 'Logout', href: '/logout' }
      ],
      author: 'Kumanote,LLC.'
    }
  },
  methods: {
    toggleDrawer() {
      this.drawer = !this.drawer
    },
    avatarMenuItemClick(href) {
      switch (href) {
        case '/logout':
          window.alert('TODO implement logout')
          break
        default:
          this.$router.push(href)
          break
      }
    }
  }
}
</script>
