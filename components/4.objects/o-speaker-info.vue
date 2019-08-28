<template>
    <div class="o-speaker-info" :class="{ reverse: reverseFlexDirection }">
        <span class="technologies">
            <b-technologies 
                v-for="(technology, index) in technologies" 
                :key="index" 
                :name="technology" />
        </span>
        <b-speaker-image :src="image" :size="400" />
        <div>
            <h3 class="large">{{ name }}</h3>
            <p class="font_color-light">{{ position }}</p>
            <div class="social">
                <b-social
                    v-for="(value, name) in socials" 
                    :key="name"
                    :name="name"
                    :href="value" />
            </div>
            <p class="padding-bottom">{{ bio }}</p>
            <h4>{{talkName}}</h4>
            <p>{{ abstract }}</p>
            <h4>Talk Goals</h4>
            <v-chip 
                v-for="(goal, index) in talkGoals" 
                :key="index">
                {{ goal }}
            </v-chip>
        </div>
    </div>
</template>

<script>
import social from '@/6.base/b-social';
import technologies from '@/6.base/b-technologies';
import speakerImage from "@/6.base/b-speaker-image";

export default {
    props:{
        reverseFlexDirection:{
            type: Boolean,
            default: false
        },
        name:{
            type: String,
            required: true
        },
        image:{
            type: String,
            required: true
        },
        position:{
            type: String,
            required: true
        },
        talkName:{
            type: String,
            required: true
        },
        bio:{
            type: String,
            required: true
        },
        abstract:{
            type: String,
            required: true
        },
        talkGoals:Array,
        socials:Object,
        technologies: Array
    },
    components:{
        'b-social': social,
        'b-speaker-image': speakerImage,
        'b-technologies': technologies
    }
}
</script>

<style lang="scss">
@import '../scss/variable/theme.scss';

.o-speaker-info{

    position: relative;
    display:flex;
    margin-bottom:100px;    
    text-align: justify;
    flex-wrap: wrap;
    min-height: 510px;
    

    & > div{
        padding: 50px 45px 0px 45px;
        max-width: 800px;
        flex:1 0 500px;
        
        @media only screen and (max-width: 960px) {
            
            flex-grow: 2;
            flex-basis: 95%;
        }
    }

    & > img{
        margin:35px auto;
        flex:0 0 auto;
        max-height: 400px;
        object-fit: cover;
    }

    .social{
        margin-bottom: 16px;
    }

    .technologies {
        position:absolute;
        bottom:0px;
        left:30px;
        z-index: 100;


        & > div{
            display: inline-block;
            margin:0px 5px;
        }
        
        @media only screen and (max-width: 960px) {
            display:none;
        }
    }

    h2{
        color:#41b883;
    }

    &.reverse{
        flex-direction: row-reverse;

        .technologies {
            right:30px;
            left:inherit;
        }
    }
}
</style>
