<template>
    <div class="archive">
        <img :src="technologyImage" class="technology" />
        <h3>{{ title }}</h3>
        <div class="speakers-container">
            <img v-for="(speaker, index) in speakers" :key="index" :src="speaker.image" :alt="speaker.name" />
        </div>
    </div>
</template>

<script>
export default {
    props:{
        title:{
            type: String,
            required: true
        },
        technologyImage:{
            type: String,
            required: true,
        },
        speakers:{
            type: Array,
            required: false
        }
    },
    computed:{
        selectedTech: function () {
            if(!this.technology.hasOwnProperty(this.name)) return;

            return this.socialList[this.name];
        }
    }
}
</script>

<style lang="scss" scoped>
.archive{
    position: relative;
    height: 300px;
    margin: 15px 10px;
    padding:35px 15px;
    background-image: url("../assets/logo-with-video.png");
    background-position: 50% 50%;
    background-repeat: no-repeat;

    &:hover{
        border-radius: 3px 3px;
        box-shadow: 5px 5px 10px grey;
    }

    .technology{
        width: 40%;
        opacity: 0.7;
        position: absolute;
        right: 0px;
        top: 0px;
        z-index:-10;
    }

    .speakers-container{
        position: absolute;
        bottom:35px;
        display: flex;
        flex-wrap: nowrap;
        justify-content: space-around;
        
        & > img{

            width:15%;
            border-radius: 50%;

        }
    }
}
</style>

