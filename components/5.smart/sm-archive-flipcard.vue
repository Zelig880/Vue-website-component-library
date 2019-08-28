<template>
    <div class="sm-archive-flipcard">
        <div class="flip-card-inner">
            <div class="flip-card-front" :class="backgroundColorClass">
                <b-speaker-image 
                    :src="image" 
                    alt="speaker image"
                    :borderColor="randomColor"/>
                <p> {{ title }}</p>
            </div>
            <div class="flip-card-back content" :class="backgroundColorClass">
                <i class="far fa-play-circle"></i>
                <p>{{ abstractSnippets }}</p>
            </div>
        </div>
    </div>
</template>

<script>

import speakerImage from "@/6.base/b-speaker-image";

export default {
    props:{
        title:{
            type: String,
            required: true
        },
        abstract:{
            type: String,
            required: true
        },
        image:{
            type:String,
            required:true
        }
    },
    data(){
        return{
            colourArray: ["red", "purple", "blue", "green", "orange"]
        }
    },
    computed: {
        abstractSnippets: function(){
            if(this.abstract.length >= 128){
                return `${this.abstract.substring(0, 125)}...`;

            }else{
                return this.abstract;
            }
            
        },
        randomColor: function(){
            const arrayLength = this.colourArray.length;
            return this.colourArray[Math.floor(Math.random()*arrayLength)];
        },
        backgroundColorClass: function(){
            return `${this.randomColor}Overlay`;

        }
    },
    components: {
      'b-speaker-image': speakerImage
    }
}
</script>

<style lang="scss">
@import '../scss/variable/theme.scss';
@import '../scss/mixins.scss';

.sm-archive-flipcard{

    background-color: transparent;
    perspective: 1000px; 
    flex:0 0 256px;
    height: 322px;
    border-radius: 4px;  
    margin:14px 16px;

    img{
        width:160px;
        height:160px;
        margin-top:28px;
        margin-bottom:24px;
        border-radius: 4px 4px 0px 4px;
    }

    @include flipCardColorOverlay(red);
    @include flipCardColorOverlay(purple);
    @include flipCardColorOverlay(blue);
    @include flipCardColorOverlay(orange);
    @include flipCardColorOverlay(green);

    .flip-card-inner {
        position: relative;
        width: 100%;
        height: 100%;
        text-align: center;
        transition: transform 0.8s;
        transform-style: preserve-3d;    
        border-radius: 4px;
    }

    &:hover .flip-card-inner {
        transform: rotateY(180deg);
    }

    .flip-card-front, .flip-card-back {
        position: absolute;
        width: 100%;
        height: 100%;
        backface-visibility: hidden;
    }

    .flip-card-front {
        background-color: $color7;
        //box-shadow:2px 2px 5px grey;
        
        p{
            font-weight: 500;
            text-align: center;
            color: $color2;
            margin:0px 24px 50px;
        }
    }

    .flip-card-back {
        transform: rotateY(180deg);
        color: $color8;

        i{
            font-size:7rem;
            margin-top:25%;
            margin-bottom:15px;
        }
    }
}
</style>
