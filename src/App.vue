<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">My App</div>

      <v-spacer></v-spacer>

      <v-btn @click="logout" v-if="isLoggedIn">
        <span class="mr-2">Logout</span>
        <v-icon>mdi-logout</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    //
  }),
  computed: {
    isLoggedIn() {
      return this.$store.getters.isAuthenticated;
    },
  },
  methods: {
    logout() {
      this.$store.dispatch("logout");
      this.$router.replace("/auth");
    },
  },
};
</script>
