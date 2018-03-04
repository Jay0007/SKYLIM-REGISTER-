<template>
    <div>
        <v-card color="" class="mb-5" height="700px">
            <v-container >
    <v-layout row wrap>
      <v-flex xs6>
        <v-subheader>10TH GRADE BOARD</v-subheader>
      </v-flex>
      <v-flex xs6>
        <v-select
          :items="items"
          v-model="e1"
          label="Select"
          single-line
          bottom
        ></v-select>
      </v-flex>
      <v-flex xs6>
        <v-subheader>10TH GRADE PERCENTAGE</v-subheader>
      </v-flex>
      <v-flex xs6>
        
      </v-flex>
      <v-flex xs6>
        <v-subheader>Error</v-subheader>
      </v-flex>
      <v-flex xs6>
        <v-select
          label="Select"
          :items="items"
          v-model="e3"
          :error-messages="['Please select an option']"
          item-value="text"
        ></v-select>
      </v-flex>
      <v-flex xs6>
        <v-subheader>Disabled</v-subheader>
      </v-flex>
      <v-flex xs6>
        <v-select
          label="Select"
          :items="items"
          v-model="e4"
          disabled
        ></v-select>
      </v-flex>
    </v-layout>
  </v-container>
        </v-card>

        <v-btn @click="consoler"></v-btn>
    </div>
</template>

<script>
  export default {
    data () {
      return {
        e1: null,
        e2: null,
        e3: null,
        e4: null,
        items: [
          { text: 'CBSE' },
          { text: 'ICSE' },
          { text: 'IB' },
          { text: 'TNSB' }
        ],
        states: [
          'Alabama', 'Alaska', 'American Samoa', 'Arizona',
          'Arkansas', 'California', 'Colorado', 'Connecticut',
          'Delaware', 'District of Columbia', 'Federated States of Micronesia',
          'Florida', 'Georgia', 'Guam', 'Hawaii', 'Idaho',
          'Illinois', 'Indiana', 'Iowa', 'Kansas', 'Kentucky',
          'Louisiana', 'Maine', 'Marshall Islands', 'Maryland',
          'Massachusetts', 'Michigan', 'Minnesota', 'Mississippi',
          'Missouri', 'Montana', 'Nebraska', 'Nevada',
          'New Hampshire', 'New Jersey', 'New Mexico', 'New York',
          'North Carolina', 'North Dakota', 'Northern Mariana Islands', 'Ohio',
          'Oklahoma', 'Oregon', 'Palau', 'Pennsylvania', 'Puerto Rico',
          'Rhode Island', 'South Carolina', 'South Dakota', 'Tennessee',
          'Texas', 'Utah', 'Vermont', 'Virgin Island', 'Virginia',
          'Washington', 'West Virginia', 'Wisconsin', 'Wyoming'
        ]
      }
    },
    methods:{
        consoler(){
            console.log(this.e1);
        }
    }
  }
</script>

