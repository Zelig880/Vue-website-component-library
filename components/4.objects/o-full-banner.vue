<template>
  <div class="o-full-banner">
    <v-parallax src="/img/background.jpg" height="1050" >
      <div class="parallax-content">
        <h1>{{ title }}</h1>
        <p class="large">{{ date }}</p>
        <p class="large">{{ time }}</p>

        <flip-countdown 
          v-if="dateIsValid" 
          :deadline="localDateTime">
        </flip-countdown>

        <sm-rsvp :eventDate="date"></sm-rsvp>

        <h2>Our Speakers</h2>
        <p class="large">{{ subheading }}</p>

        <div class="speaker-image-container">
          <b-speaker-image 
            v-for="(speaker, index) in speakers" 
            :key="index" 
            :src="speaker.image" 
            :size="300" />
        </div>
      </div>
    </v-parallax>
  </div>
</template>

<script>
import rsvp from "@/5.smart/sm-rsvp";
import speakerImage from "@/6.base/b-speaker-image";
import FlipCountdown from 'vue2-flip-countdown'
import moment from 'moment';

export default {
  props:{
    title:{
      type: String,
      default: `${process.env.VUE_APP_THEME} meetup`
    },
    subheading:{
      type:String,
      default: `Join us for ${process.env.VUE_APP_THEME}-specific talks every month in the comfort of your own home -- where ever you are in the world!`
    },
    date:{
      type: String,
      required: true
    },
    time:{
      type: String,
      required: true
    },
    fullDateTime:{
      type: String,
      required: true
    },
    speakers: Array
  },
  computed:{
    dateIsValid(){
      var dateIsValid = moment(this.fullDateTime).isValid();
      var dateIsInTheFuture = moment(this.fullDateTime).isAfter();
      return dateIsValid && dateIsInTheFuture;
    },
    localDateTime(){
      if(this.dateIsValid){
        const date = moment.utc(this.fullDateTime);

        return date.local().format("LLL");
      }
    }
  },
  components:{
    'sm-rsvp': rsvp,
    'b-speaker-image': speakerImage,
      FlipCountdown
  }
}
</script>


<style lang="scss">

.o-full-banner {

  position: relative;
  margin-bottom:50px;
  
  & > div{    
    margin-left: -50vw;
    left: 50%;
    width: 100vw;

    i.v-icon  {
      font-size: 1.1em;
    }
    .v-parallax__image{
      transform: scale(1.5)
    }
    .parallax-content{
      max-width:1280px;
      margin: 0 auto;
      text-align: center;
      
      h1, h2{    
        letter-spacing: 0.02em;
        color: white;
        margin-bottom:35px;
      }

      p{

        color: white;
        font-weight: 500;
        line-height: 125%;
      }

      button{
        margin-top:25px;
      }
    }

    .speaker-image-container{
        @media only screen and (max-width: 960px) {
            display:none;
        }
    }
  }
  
  & > button{
    position:absolute;
    left: calc(50% - 28px);
    bottom:-36px;
  }
}
</style>
