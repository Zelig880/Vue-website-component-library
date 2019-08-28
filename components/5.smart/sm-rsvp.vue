<template>
    <div class="sm-rsvp text-xs-center">
      <v-dialog
        v-model="dialog"
        width="500"
      >
        <template v-slot:activator="{ on }">
            <button @click="dialog = true">ATTEND</button>
        </template>
  
        <v-card>
          <v-card-title
            class="display-1 lighten-2"
            primary-title
          >
            Register to the event
          </v-card-title>
  
          <v-card-text>
            <v-text-field
              label="Your name*"
              box
              v-model="name"
              required="required"
            ></v-text-field>
            <v-text-field
              label="Email Address*"
              box
              v-model="email"
              name="email"
              :error-messages="emailErrors"
            ></v-text-field>
            <v-text-field
              label="Company"
              v-model="company"
              box
            ></v-text-field>
            <v-text-field
              label="Position"
              v-model="position"
              box
            ></v-text-field>
          </v-card-text>
  
          <v-divider></v-divider>
  
          <v-card-actions>
            <v-spacer></v-spacer>
            <button @click="submitForm">RSVP</button>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </div>
</template>

<script>
var currentTheme = process.env.VUE_APP_THEME.trim();

export default {
  props:{
    eventDate: String
  },
  data () {
    return {
      dialog: false,
      email: "",
      name: "",
      company: "",
      position: "",
      emailErrors: []
    }
  },
  methods:{
    submitForm(){
       
      if(!this.validateEmail("email", "emailErrors")) return;

      var params = {
          "email": this.email,
          "merge_fields": {
            "Registration_type": `${currentTheme}-${this.eventDate}`,
            "name": this.name,
            "position": this.position,
            "company": this.company
          }
      }

      this.addContactToMailingList(process.env.VUE_APP_MAILCHIMP_NEWSLETTER_LIST_ID, params);
      this.dialog = false;
    },
    validateEmail(field, fieldError){
        const emailRegex = /.+@.+\..+/;
        this[fieldError] = [];

        if(this[field].length === 0){ 
            this[fieldError].push("An email is required."); 
            return false;
        }else if(!emailRegex.test(this[field])){
            this[fieldError].push("The email address is not valid."); 
            return false;
        }

        return true;
    }
  }
}
</script>

<style lang="scss">
@import '../scss/variable/theme.scss';

  .sm-rsvp button{
    width:179px;
    height:52px;
    color: white;
    border-radius: 4px;
    margin:40px 0;
    background-color:$color6 !important;
    font-weight: 600;
    font-size: 20px;
    letter-spacing: 0.04em;
  }
</style>
