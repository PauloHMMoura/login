<style scoped>
    /*.transparento {
    background-color: rgba(255, 255, 255, 0.527) !important;
  }*/
</style>

<template>
    <v-flex style="margin-top:20px;" xs12 sm8 offset-sm2>
        <v-stepper style="border-radius:10px;" v-model="e1">
            <!--head text-->
            <v-flex xs12 text-xs-center>
                <h1 style="margin-top:10px; margin-bottom:10px;">REGISTER</h1>
            </v-flex>
            <v-stepper-header style="height: 85px;">
                <v-stepper-step :complete="e1 > 1" step="1">Information</v-stepper-step>

                <v-divider></v-divider>

                <v-stepper-step :complete="e1 > 2" step="2">Membership Type</v-stepper-step>

                <v-divider></v-divider>

                <v-stepper-step step="3">Conclusion</v-stepper-step>
            </v-stepper-header>

            <!--first section-->

            <v-stepper-items>
                <v-stepper-content step="1">
                    <v-card>
                        <form>

                            <v-text-field outline v-model="name" v-validate="'required|max:20'" :counter="20"
                                :error-messages="errors.collect('name')" label="Username" data-vv-name="name" required>
                            </v-text-field>

                            <v-text-field outline v-model="email" v-validate="'required|email'"
                                :error-messages="errors.collect('email')" label="E-mail" data-vv-name="email" required>
                            </v-text-field>

                            <v-text-field outline v-model="password" :error-messages="passwordErrors" label="Password"
                                required @input="$v.email.$touch()" @blur="$v.email.$touch()"></v-text-field>

                            <v-text-field outline v-model="brokerage" :rules="BrokerageRules" label="Brokerage">
                            </v-text-field>

                            <v-text-field outline v-model="phone" :rules="PhoneRules" label="Phone Number" required>
                            </v-text-field>


                        </form>
                    </v-card>

                    <div style="margin-top:10px;">
                        <v-btn color="primary" @click="e1 = 2">
                            Continue
                        </v-btn>

                        <v-btn flat to="/Home">Cancel</v-btn>
                    </div>
                </v-stepper-content>

                <!--Second section-->

                <v-stepper-content step="2">
                    <v-flex xs12 text-xs-center>
                        <h2 style="margin-bottom: 10px;">SELECT PLAN</h2>
                    </v-flex>
                    <v-card>
                        <v-item-group>
                            <v-container grid-list-md>
                                <v-layout wrap>
                                    <v-flex v-for="n in 3" :key="n" xs12 md4>
                                        <v-item>
                                            <v-card slot-scope="{ active, toggle }" :color="active ? 'primary' : ''"
                                                class="d-flex align-center" dark height="200" @click="toggle">
                                                <v-scroll-y-transition>
                                                    <div v-if="active" class="display-3 text-xs-center activated">
                                                        <div style="display:none;">{{m=n-1}}</div>
                                                        {{n}}
                                                    </div>
                                                </v-scroll-y-transition>

                                                <v-flex>
                                                <div> {{plans.planName[n-1]}} </div>
                                                <div> {{plans.planDesc[n-1]}} </div>
                                                <div> Value:{{plans.planPrice[n-1]}} </div>
                                                </v-flex>
                                            </v-card>

                                        </v-item>
                                    </v-flex>
                                </v-layout>
                            </v-container>
                        </v-item-group>
                    </v-card>

                    <div style="margin-top:10px;">
                        <v-btn color="primary" @click="e1 = 3">
                            Continue
                        </v-btn>

                        <v-btn flat @click="e1 = 1">Go Back</v-btn>
                    </div>
                </v-stepper-content>

                <!--Section 3-->

                <v-stepper-content step="3">
                    <v-flex xs12 text-xs-center>
                        <h2 style="margin-bottom: 10px;">SUMMARY</h2>
                    </v-flex>

                    <v-card class="mb-5" color="lighten-1" height="200px">

                        <br>

                        <v-flex xs12 sm8 offset-sm2>
                        <div>Name: {{name}}</div>
                        <div>Email: {{email}}</div>
                        <div>Brokerage: {{brokerage}}</div>
                        <div>Phone: {{phone}}</div>

                        <br>

                        <div>Selected Plan: {{plans.planName[m]}}</div>
                        <div>Description: {{plans.planDesc[m]}}</div>
                        <div>Value: {{plans.planPrice[m]}}</div>
                        </v-flex>
                        <!--plan type-->
                        <!--value to pay-->
                    </v-card>

                    <div style="margin-top:10px;">
                        <v-btn color="primary" @click="e1 = 1">
                            SUBMIT
                        </v-btn>

                        <v-btn flat @click="e1 = 2">Go Back</v-btn>
                    </div>
                </v-stepper-content>
            </v-stepper-items>
        </v-stepper>
    </v-flex>
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

            plans: {
                planName: ['One', 'Two', 'Three'],
                planDesc: ['Free First Month', 'Monthly', 'Billed Annually'],
                planPrice: ['Free*', '$24.99', '$19.99/m']
            },
            //stepper data
            e1: 0,

            m: 0,
            name: '',
            email: '',
            checkbox: null,
            dictionary: {
                attributes: {
                    email: 'E-mail Address'
                    // custom attributes
                },
                custom: {
                    name: {
                        required: () => 'Name can not be empty',
                        max: 'The Username field may not be greater than 20 characters'
                        // custom messages
                    },
                    //not being used, can be used for newsletter etc.
                    select: {
                        required: 'Select field is required'
                    }
                }
            }
        }),

        mounted() {
            this.$validator.localize('en', this.dictionary)
        },

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