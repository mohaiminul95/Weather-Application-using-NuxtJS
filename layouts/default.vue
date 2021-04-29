<template>
<v-app style="background: #fff;">
  <v-card
    color="grey lighten-4"
    flat
    tile
  >
    <v-toolbar dense color="indigo" dark>

      <v-toolbar-title>
        <nuxt-link to='/'>Weather Application</nuxt-link>
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn >
          <nuxt-link to='/'>Home</nuxt-link>
        </v-btn>
        <v-btn >
          <nuxt-link to='/weather'>Check Weather</nuxt-link>
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>
  </v-card>

  <v-content>
    <nuxt/>
  </v-content>

  
</v-app>
</template>

<script>
export default {
  
}
</script>


<style>
  .v-btn:not(.v-btn--round).v-size--default {
      background: transparent;
      border: none;
      box-shadow: none;
    }
  .v-application a {
    text-decoration: none;
    color: #fff!important;
  }
</style>