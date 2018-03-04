<template>
    <div id="app">
        <v-app id="inspire">
            <navbar class="mb-2"></navbar>
            <v-stepper v-model="e1">
                <v-stepper-header>
                    <v-stepper-step step="1" :complete="e1 > 1">PERSONAL DETAILS</v-stepper-step>
                    <v-divider></v-divider>
                    <v-stepper-step step="2" :complete="e1 > 2">EDUCATIONAL BACKGROUND</v-stepper-step>
                    <v-divider></v-divider>
                    <v-stepper-step step="3">COURSE DETAILS</v-stepper-step>
                    <v-divider></v-divider>
                    <v-stepper-step step="4">FEE STRUCTURE</v-stepper-step>
                </v-stepper-header>
                
                <v-stepper-items>
                    <v-stepper-content step="1">
                        <one :complete="e1"></one>
                        <v-btn color="primary" @click.native="e1 = 2">Continue</v-btn>                        
                    </v-stepper-content>
                    <v-stepper-content step="2">
                        <two></two>
                        <v-btn color="primary" @click.native="e1 = 3">Continue</v-btn> 
                        <v-btn color="primary" @click.native="e1 = 1">Go Back</v-btn>                        
                       
                    </v-stepper-content>
                    <v-stepper-content step="3">
                        <three></three>
                        <v-btn color="primary" @click.native="e1 = 1">Continue</v-btn>
                        <v-btn flat>Cancel</v-btn>
                    </v-stepper-content>
                </v-stepper-items>

            </v-stepper>
        </v-app>
    </div>
</template>
  
<script>

import navbar from './../navbar.vue'

import one from './steps/one.vue'
import two from './steps/two.vue'
import three from './steps/three.vue'

export default {
  data () {
    return {
      e1: 0
    }
  },
  components:{navbar,one,two,three}
}
</script>