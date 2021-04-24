<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
      clipped-left
    >
<!--      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>-->
      <v-toolbar-title>
        <h4>Sonetos de Terras de Ara</h4>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn text to="/">
        <span class="mr-2">Home</span>
      </v-btn>
      <v-btn text to="/Sonetos">
        <span class="mr-2">Sonetos</span>
      </v-btn>
      <v-btn text href="http://5a134398af42.ngrok.io/accounts/facebook/login/">
        <span class="mr-2">Login</span>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>
    <br>
    <v-footer absolute>
      <v-col
          class="text-center"
          cols="12"
      >
        {{ new Date().getFullYear() }} — <strong>Itamar Souto  © </strong>
      </v-col>
    </v-footer>
  </v-app>
</template>
