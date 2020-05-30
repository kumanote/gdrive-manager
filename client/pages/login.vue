<template>
  <v-row align="center" justify="center">
    <v-col cols="12" sm="8" md="6" lg="4">
      <v-card class="elevation-12">
        <v-toolbar color="primary" flat>
          <v-toolbar-title>GDrive Manager</v-toolbar-title>
          <v-spacer />
        </v-toolbar>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="secondary"
            large
            class="mr-2 mb-2"
            @click.stop="authenticate"
            >Login with Google</v-btn
          >
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  auth: false,
  layout: 'centered',
  methods: {
    authenticate() {
      this.$auth.loginWith('app')
    }
  }
}
</script>
