<template>
  <v-parallax src="/img/background.jpeg" class="parallax2" >
    <div class="parallax-content">
      <div>
        <h1 class="display-3">Vue Conference online</h1>
        <h2 class="display-2">28th of September 2019</h2>
        <v-btn raised large>RSVP</v-btn>
      </div>
      <div>
        <img src="/img/speakers/avatar1.jpg">
      </div>
    </div>
  </v-parallax>
</template>

<style lang="scss">
.parallax2{    
    margin-left: -50vw;
    left: 50%;
    width: 100vw;

    .v-parallax__content{
      background:linear-gradient(90deg,#41b883 0%,rgba(255,255,255,0.001) 100%); //vue color left to rigth
    }

    .parallax-content{

      max-width:1280px;
      margin: 0 auto;
      text-align: center;      
      display:flex;
      & > div{
        align-self: center;
      }
      
      h1,h2{
        color: white;
      }
      
      img{

        height: 60%;
        margin: auto;
        position: relative;
        filter: grayscale(1);
        transform: rotate(18deg);
        padding:15px 10px;
        background-color: #41b883;
      }

      button{
        width:200px;
        height:75px;
      }
    }
  }
</style>
