<template>
  <v-row justify="center">
    <v-col cols="12" md="8">
      <p class="display-1">{{ title }}</p>
    </v-col>
  </v-row>
</template>

<script>
export default {
  auth: false,
  data() {
    return {
      title: 'GDrive Manager'
    }
  },
  mounted() {
    if (this.$auth.loggedIn) {
      this.$router.push('/home')
    } else {
      this.$router.push('/login')
    }
  }
}
</script>
