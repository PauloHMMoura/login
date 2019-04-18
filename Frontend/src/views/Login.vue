<style scoped>
  .transparento {
    background-color: rgba(255, 255, 255, 0.699) !important;
    border-radius: 10px;
  }

  .v-input__slot {
    background-color: white !important;
  }
</style>

<template>
  <form>
    <v-flex xs12 sm6 offset-sm3>
      <v-card style="padding:10px; margin-top:20px;" class="transparento">

        <v-flex text-xs-center>
          <h1 style="margin-top:10px;">LOGIN</h1>
        </v-flex>

        <br>

        <v-text-field outline v-model="name" v-validate="'required|max:20'" :error-messages="errors.collect('name')"
          label="Username" data-vv-name="name" required></v-text-field>

        <v-text-field outline v-model="password" :append-icon="show1 ? 'visibility' : 'visibility_off'"
          :rules="[rules.required, rules.min]" :type="show1 ? 'text' : 'password'" name="input-10-1"
          label="Password" @click:append="show1 = !show1" v-validate="'required'" :error-messages="errors.collect('password')" data-vv-name="password" required>
        </v-text-field>

        <v-checkbox v-model="remember" v-validate="" :error-messages="errors.collect('checkbox')" value="1"
          label="Remember Me" data-vv-name="checkbox" type="checkbox"></v-checkbox>

        <div class="text-xs-center">
          <v-btn align-center @click="submit" large color="primary">SIGN IN</v-btn>
          <br><br>

          <h3>Don't have an account?<v-btn to="/Register" flat color="primary" dark> Sign up</v-btn>
          </h3><br>
          <a>Forgot password?</a>

        </div>
      </v-card>
    </v-flex>
  </form>
</template>

<script>
  import Vue from 'vue'
  import VeeValidate from 'vee-validate'

  Vue.use(VeeValidate)

  export default {
    $_veeValidate: {
      validator: 'new'
    },

    data: () => ({
      name: '',
      password: '',
      checkbox: null,

      show1: false,
        rules: {
          //required: value => !!value || 'Required.',
          emailMatch: () => ('The email and password you entered don\'t match')
        },

      dictionary: {
        attributes: {
          password: 'Password'
          // custom attributes
        },
        custom: {
          name: {
            required: () => 'Please insert your username',
            max: 'The Username field may not be greater than 20 characters'
            // custom messages
          },
          select: {
            required: 'Select field is required'
          }
        },
        custom: {
          password: {
            required: () => 'Please insert your password'
            // custom messages
          },
          select: {
            required: 'Select field is required'
          }
        }
      }
    }),

    mounted() {
      this.$validator.localize('en', this.dictionary)
    },

    methods: {
      submit() {
        this.$validator.validateAll()
      }
    }
  }
</script>




<!--<template>
    <v-layout row wrap>
        {{info.data.chartName}}
    </v-layout>
    
</template>

<script>
  
  export default {
   data () {
    return {
      info: null
    }
  },
  mounted () {
    axios
      .get('https://api.coindesk.com/v1/bpi/currentprice.json')
      .then(response => (this.info = response))
  }
  }
</script>-->