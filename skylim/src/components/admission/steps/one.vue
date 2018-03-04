<template>
    <div>
        <v-card color="" class="mb-5" height="700px">
            <v-form v-model="valid">
                <v-container grid-list-md text-xs-center>
                    
                    
                    <!--profile picture card-->
                    <v-flex xs4 offset-xs4>
          <v-card-media
            :src="image"
            height="190px"
            contain
          >
          </v-card-media>

          
              <input type="file" class="form-control-file ml-5 pl-2 mt-3 mb-4" id="fileInput" @change="onFileChange">

                    </v-flex>
                    
                 <!--profile picture card-->   
                    
                
                    <h2>STUDENT'S DETAILS</h2>
                   
                    <v-layout row>
    
                        <v-flex xs4 mr-4>
                            <v-text-field label="First Name" :rules="nameRules" :counter="10" required></v-text-field>
                        </v-flex>
    
                        <v-flex xs4 mr-4>
                            <v-text-field label="Middle Name (Optional)" :rules="nameRules" :counter="10"></v-text-field>
                        </v-flex>
    
                        <v-flex xs4>
                            <v-text-field label="Last Name" :rules="nameRules" :counter="10"></v-text-field>
                        </v-flex>
    
                    </v-layout>
    
                    <v-layout row class="text-md-center">
                        <v-flex xs2>        <v-radio :label="`Male`" :key=0 :value=0></v-radio></v-flex>
                        <v-flex xs2>        <v-radio :label="`Female`" :key=1 :value=0></v-radio></v-flex>

                        <v-menu
      ref="menu"
      lazy
      :close-on-content-click="false"
      v-model="menu"
      transition="slide-y-transition"
      offset-y
      bottom
      center
      full-width
      :nudge-right="40"
      min-width="290px"
    >
      <v-text-field
        slot="activator"
        label="D.O.B"
        v-model="date"
        prepend-icon="event"
        readonly
      ></v-text-field>
      <v-date-picker
        landscape=""
        ref="picker"
        v-model="date"
        @change="save"
        min="1950-01-01"
        :max="new Date().toISOString().substr(0, 10)"
      ></v-date-picker>
    </v-menu>


                    </v-layout>


                    <h2>FATHER'S DETAILS</h2>

                    <v-layout row>
    
                        <v-flex xs4 mr-4>
                            <v-text-field label="First Name" :rules="nameRules" :counter="10" required></v-text-field>
                        </v-flex>
    
                        <v-flex xs4 mr-4>
                            <v-text-field label="Middle Name (Optional)" :rules="nameRules" :counter="10"></v-text-field>
                        </v-flex>
    
                        <v-flex xs4>
                            <v-text-field label="Last Name" :rules="nameRules" :counter="10"></v-text-field>
                        </v-flex>
    
    
                    </v-layout>




                    <h2>MOTHER'S DETAILS</h2>
                   
                    <v-layout row>
    
                        <v-flex xs4 mr-4>
                            <v-text-field label="First Name" :rules="nameRules" :counter="10" required></v-text-field>
                        </v-flex>
    
                        <v-flex xs4 mr-4>
                            <v-text-field label="Middle Name (Optional)" :rules="nameRules" :counter="10"></v-text-field>
                        </v-flex>
    
                        <v-flex xs4>
                            <v-text-field label="Last Name" :rules="nameRules" :counter="10"></v-text-field>
                        </v-flex>
    
                    </v-layout>


                </v-container>
            </v-form>
        </v-card>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                valid: false,
                image:'https://museum.wales/media/40374/thumb_480/empty-profile-grey.jpg',
                date: null,
                menu: false,
                name: '',
                nameRules: [
                    v => !!v || 'Name is required',
                    v => v.length <= 10 || 'Name must be less than 10 characters'
                ],
                email: '',
                emailRules: [
                    v => !!v || 'E-mail is required',
                    v => /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v) || 'E-mail must be valid'
                ]
            }
        },

watch: {
  menu (val) {
    val && this.$nextTick(() => (this.$refs.picker.activePicker = 'YEAR'))
  }
},
methods: {
  save (date) {
    this.$refs.menu.save(date)
  },
  onFileChange(e) {
      var files = e.target.files || e.dataTransfer.files;
      if (!files.length)
        return;
      this.createImage(files[0]);
    },
    createImage(file) {
      var image = new Image();
      var reader = new FileReader();
      var vm = this;

      reader.onload = (e) => {
        vm.image = e.target.result;
      };
      reader.readAsDataURL(file);
    },
    removeImage: function (e) {
      this.image = '';
    }
}
    }
</script>
