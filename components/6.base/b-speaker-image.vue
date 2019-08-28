<template>
    <img 
        :src="src" 
        :alt="alt" 
        :width="width" 
        :height="height"
        :style="{boxShadow: boxShadow}" />
</template>

<script>
export default {
    props:{
        src:{
            type:String,
            required: true
        },
        alt:{
            type:String,
            default:"Speaker image"
        },
        size:{
            type:Number,
            required:false,
            default:160
        },
        borderColor:{
            type:String
        }
    },
    data(){
        return{
            colourArray: {
                "red": "red", 
                "purple": "purple", 
                "yellow": "yellow", 
                "green": "green",
                "orange": "orange"
            }
        }
    },
    computed:{
        width(){
            return `${this.size}px`;
        },
        height(){
            return `${this.size}px`;
        },
        defaultBorderColor(){
            return this.$global[`${this.$global.theme}Primary`];
        },
        boxShadow(){

            let color = this.defaultBorderColor;
            let size = this.size / 40; // 1/4 of the size in proportion

            if(this.colourArray.hasOwnProperty(this.borderColor)){
                color = this.colourArray[this.borderColor];
            }


            return  `${size}px ${size}px ${color}`;
        }
    }
}
</script>

<style lang="scss" scoped>

    img{
        margin:28px 50px 24px 50px;
        border-radius: 4px 4px 0px 4px;
    
        @media only screen and (max-width: 960px) {
            margin:28px 10px 24px 10px;
            width:80%;
            height: auto;
        }
    }
</style>
