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
    <!--fontawesome icons load-->
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.8.1/css/all.css" integrity="sha384-50oBUHEmvpQ+1lW4y57PTFmhCaXp0ML5d60M1M7uH2+nqUivzIebhndOJK28anvf" crossorigin="anonymous">
    <link rel="shortcut icon" href="./assets/logo.png">

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

    <!--footer-->
    <v-footer style="margin-top:20px;" dark height="auto">
      <v-card class="flex" flat tile>
        <v-card-title style="height: 60px;" class="red">
          <strong class="subheading"></strong>

          <v-spacer></v-spacer>

          <div style="margin-top: -10px;">
            <v-btn v-for="icon in icons" :key="icon" class="mx-3" dark icon>
            <v-icon size="24px">{{ icon }}</v-icon>
          </v-btn>
          </div>
        </v-card-title>

        <v-card-actions class="grey darken-3 justify-center">
          &copy;2019 — <strong>RA.CA</strong>
        </v-card-actions>
      </v-card>
    </v-footer>

  </v-app>
</template>

<script>
  import HelloWorld from './components/HelloWorld'

  export default {
    name: 'App',
    components: {
      HelloWorld
    },
    data: () => ({
      icons: [
        'fab fa-facebook',
        'fab fa-twitter',
        'fab fa-linkedin',
        'fab fa-instagram'
      ]
    })
  }
</script>