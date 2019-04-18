<style scoped>
  .pad {
    margin: 10px;
  }

  .padless {
    margin: 0px;
  }

  .arranged {
    margin-right: 10px;
  }

  .searchtab {
    margin-right: 10px;
  }

  @media only screen and (max-width: 600px) {
    .arranged {
      margin-right: 0px;
      margin-bottom: 0px;
    }

    .pad {
      margin: 5px;
    }

    .searchtab {
      margin-right: 0px;
    }
  }
</style>

<template>
  <v-layout row wrap pad>
    <v-flex xs4 sm3>
      <v-card class="arranged" dark>
        <v-card-text class="padless"><span style="padding:10px;">Address:</span></v-card-text>
      </v-card>
    </v-flex>
    <v-flex xs8 sm9>
      <v-card dark>
        <v-card-text class="padless"><span style="padding:10px;">Current Address</span></v-card-text>
      </v-card>
    </v-flex>

    <v-flex xs12 sm3>

      <v-flex>
        <v-card class="arranged">
          <v-card-text class="pad">Search Filters</v-card-text>
        </v-card>
      </v-flex>

      <v-card class="searchtab">
        <v-container fill-height fluid>
          <v-layout fill-height>
            <v-flex xs12 align-end flexbox>
              <span class="headline">Search Values</span>
            </v-flex>
          </v-layout>
        </v-container>

        <v-card-title>
          <div>
            <span class="grey--text">info0</span><br>
            <span>info1</span><br>
            <span>info2</span>
          </div>
        </v-card-title>
      </v-card>

    </v-flex>

    <v-flex xs12 sm9>

      <v-flex>
        <v-card pad>
          <v-card-text class="pad">Search Results:</v-card-text>
        </v-card>
      </v-flex>

      <v-card>
        <v-img class="white--text" height="200px" src="https://cdn.vuetifyjs.com/images/cards/docks.jpg">
          <v-container fill-height fluid>
            <v-layout fill-height>
              <v-flex xs12 align-end flexbox>
                <span class="headline">TITLE</span>
              </v-flex>
            </v-layout>
          </v-container>
        </v-img>
        <v-card-title>
          <div>
            <span class="grey--text">placehold</span><br>
            <span>info1</span><br>
            <span>info2</span>
          </div>
        </v-card-title>
        <v-card-actions>
          <v-btn flat color="red">Share</v-btn>
          <v-btn flat color="red">Book Now</v-btn>
        </v-card-actions>
      </v-card>

    </v-flex>

  </v-layout>
</template>

<script>
  import Vue from 'vue'

  export default {
    data: () => ({
      lorem: `Lorem ipsum dolor sit amet, mel at clita quando. Te sit oratio vituperatoribus, nam ad ipsum posidonium mediocritatem, explicari dissentiunt cu mea. Repudiare disputationi vim in, mollis iriure nec cu, alienum argumentum ius ad. Pri eu justo aeque torquatos.`
    })
  }
</script>