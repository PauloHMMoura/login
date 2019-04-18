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
    margin-top: 7px;
  }

  #drawer {
    background: rgba(240, 240, 240, 0);

  }
</style>

<template>
  <v-app>
    <!--fontawesome icons load-->
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.8.1/css/all.css"
      integrity="sha384-50oBUHEmvpQ+1lW4y57PTFmhCaXp0ML5d60M1M7uH2+nqUivzIebhndOJK28anvf" crossorigin="anonymous">
    <link rel="shortcut icon" href="./assets/logo.png">

    <!--REALTOR RED #D12027-->
    <v-toolbar app style="background-color:white;">
      <v-toolbar-title class="headline text-uppercase">
        <!--<v-btn to="/Home">--><a href="app.vue"><img class="logologo" src="./assets/logotemplate2.svg"></a>
      </v-toolbar-title>
      <v-spacer></v-spacer>


      <v-toolbar-side-icon @click.stop="drawer = !drawer" class="hidden-md-and-up"></v-toolbar-side-icon>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn flat to="/Home" >Home</v-btn>
        <v-btn flat to="/Servlist" >Listings</v-btn>
        <v-btn flat to="/Login" >Login</v-btn>

      </v-toolbar-items>

      <v-navigation-drawer v-model="drawer" temporary absolute width="600" id="drawer">
      </v-navigation-drawer>

    </v-toolbar>

    <v-content>
      <router-view></router-view>
    </v-content>

    <!--footer-->
    <v-footer style="margin-top:20px;" dark height="auto">
      <v-card class="flex" flat tile>

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

      menu: [{
          icon: 'home',
          title: 'Login'
        },
        {
          icon: 'info',
          title: 'Listings'
        },
        {
          icon: 'search',
          title: 'Favourites'
        }
      ]

    }),

    methods: {
      menuItems() {
        return this.menu
      }
    }
  }
</script>