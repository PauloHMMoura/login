<style scoped>
  .theme--light.application {
    background: rgba(255, 255, 255, 0.904);
    color: rgba(0, 0, 0, 0.87);
  }

  .transparento {
    background-color: rgba(255, 255, 255, 0.384) !important;
  }

  .logologo {
    width: 100%;
    margin-top: 6px;
  }
</style>

<template>
  <v-app>
    <v-toolbar app style="background-color:red;">
      <v-toolbar-title class="headline text-uppercase">
        <!--<v-btn to="/Home">--><a href="app.vue"><img class="logologo" src="./assets/logotemplate1.svg"></a>
      </v-toolbar-title>
      <v-spacer></v-spacer>

      <v-btn to="/Login" color="error" dark @click="expand = !expand">Login</v-btn>


    </v-toolbar>

    <v-content>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>
  import HelloWorld from './components/HelloWorld'

  export default {
    name: 'App',
    components: {
      HelloWorld
    },
    data() {
      return {
        //
      }
    }
  }
</script>