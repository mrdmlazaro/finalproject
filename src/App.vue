<template>
  <v-app class="vapp">
    <v-toolbar color="#FFA500" app>
      <v-toolbar-title><a href="/">QN'A</a></v-toolbar-title>
      <v-spacer></v-spacer>

      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn class="selection" v-if="loggedIn==true" flat to="/">Home</v-btn>
        <v-btn class="selection" v-if="loggedIn==true" flat to="/about">About</v-btn>
        <v-btn class="selection" v-if="loggedIn==true" flat @click="submitLogout">Logout</v-btn>
        <v-btn class="selection" v-if="loggedIn==false" to="/login" flat>Login</v-btn>
        <v-btn class="selection" v-if="loggedIn==false" to="/register" flat>Register</v-btn>
      </v-toolbar-items>

    </v-toolbar>
    <v-content>
      <v-container fluid>
        <router-view></router-view>
      </v-container>
    </v-content>
    <v-footer app></v-footer>
  </v-app>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  name: 'app',
  data() {
    return {
      loggedIn: false,
    }
  },

  methods: {
    ...mapActions('user', {
      logout: 'logout',
    }),

    submitLogout() {
      this.logout().then(response => {
        this.$router.replace('login')
        location.reload()
      })
    },

    loginCheck() {
      this.loggedIn = this.$store.state.user.loggedIn
    },

  },

  created() {
    this.loginCheck()
  }
};

</script>

<style>
@font-face {
  font-family: "Gotham Bold";
  src: local("Gotham"),
    url(./fonts/Gotham/GothamBold.ttf) format("truetype");
}

@font-face {
  font-family: "Gotham Medium";
  src: local("Gotham"),
    url(./fonts/Gotham/GothamMedium.ttf) format("truetype");
}

.v-toolbar__title a {
  text-decoration: none;
  font-family: "Gotham Black", Helvetica, Arial;
  color: rgb(0, 0, 0)
}
.v-btn{
  text-decoration: none;
  font-family: "Gotham Black", Helvetica, Arial;
  color: rgb(255, 255, 255)
}

</style>
