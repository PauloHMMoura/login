<style scoped>

  .transparento {
    background-color: rgba(255, 255, 255, 0.527) !important;
  }

</style>

<template>
<v-container grid-list-xs>
  <v-layout row wrap>
        <v-flex xs12>
          <v-card class="transparento">
            <v-card-title primary-title>
              <div>
                <h3 class="headline mb-0"><h1>Home</h1><br>main page</h3>
                <div>{{info}}</div>
              </div>
            </v-card-title>
            <v-card-actions>
              <v-btn flat color="primary"></v-btn>
              <v-btn flat color="primary">Listings</v-btn>
            </v-card-actions>
          </v-card>
        </v-flex>
    </v-layout>
</v-container>
    
</template>

<script>
  
  export default {
    data :{
      info: "some text"  
       
    }
   
  }
</script>
