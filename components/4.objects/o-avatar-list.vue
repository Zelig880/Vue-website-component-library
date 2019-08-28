<template>
    <v-flex>
        <h2 class="text-center">{{ title }}</h2>
        <v-expansion-panel popout>
            <v-expansion-panel-content
            v-for="(message, i) in messages"
            :key="i"
            hide-actions
                flex md12 lg6
            >
            <template v-slot:header >
                <v-layout
                align-center
                spacer
                >
                <v-flex xs4 sm2 md3>
                    <v-avatar size="36px">
                      <img
                          :src="message.avatar"
                          alt="Avatar"
                      >
                    </v-avatar>
                </v-flex>
    
                <v-flex sm5 md6>
                    <strong v-html="message.name"></strong>
                    <div class="caption">Web Developer</div> 
                </v-flex>
    
                <v-flex no-wrap xs5 sm3 md3 hidden-xs-only>
                    <img src="../assets/react.png" width="30px" class="technology" alt="speaker1" />
                    <img src="../assets/vue.png" width="30px" class="technology" alt="speaker1" />
                    <img src="../assets/angular.png" width="30px" class="technology" alt="speaker1" />
                </v-flex>
                </v-layout>
            </template>
    
            <v-card>
                <v-divider></v-divider>
                <v-card-text v-text="message.lorem"></v-card-text>
            </v-card>
            </v-expansion-panel-content>
        </v-expansion-panel>
    </v-flex>
</template>

<script>
export default {
  props:{
    title:{
      type: String,
      required: true
    }
  },
  data: () => ({
    messages: [
      {
        avatar: 'https://avatars0.githubusercontent.com/u/9064066?v=4&s=460',
        name: 'John Leider',
        title: 'Welcome to Vuetify.js!',
        lorem: "This is my bio, I am a very good web dev.. my mum told me so.."
      },
      {
        avatar: 'https://avatars0.githubusercontent.com/u/9064066?v=4&s=460',
        name: 'Social',
        title: 'Twitter',
        lorem: "ciao"
      },
      {
        avatar: 'https://avatars0.githubusercontent.com/u/9064066?v=4&s=460',
        name: 'Promos',
        title: 'Shop your way',
        lorem: "sum dolor sit amet, at a"
      }
    ],
    lorem: 'Lorem ipsum dolor sit amet, at aliquam vivendum vel, everti delicatissimi cu eos. Dico iuvaret debitis mel an, et cum zril menandri. Eum in consul legimus accusam. Ea dico abhorreant duo, quo illum minimum incorrupte no, nostro voluptaria sea eu. Suas eligendi ius at, at nemore equidem est. Sed in error hendrerit, in consul constituam cum.'
  })
}
</script>

