<template>
    <a class="b-social" :title="name" :class="{ lightTheme: lightTheme }" rel="noopener" :href="href" target="_blank">
        <i :class="selectedSocial"></i>
    </a>
</template>

<script>
export default {
    props:{
        name: {
            type: String,
            required: true,
            validator: function (value) {
                return ['facebook', 'twitter', 'youTube', 'medium', 'github', 'devto'].indexOf(value) !== -1
            }
        },
        href:{
            type: String
        },
        lightTheme:{
            type: Boolean,
            default: false
        }
    },
    data(){
        return {
            socialList:{
                facebook:"fab fa-facebook-square",
                twitter:"fab fa-twitter-square",
                youTube:"fab fa-youtube-square",
                medium:"fab fa-medium",
                github:"fab fa-github-square",
                devto: "fab fa-dev"
            }
        }
    },
    computed:{
        selectedSocial: function () {
            if(!this.socialList.hasOwnProperty(this.name)) return;

            return this.socialList[this.name];
        }
    }
}
</script>
<style lang="scss">
.b-social{
    font-size:20px;
    margin:0px 5px;
    padding:5px;
    cursor: pointer;
    &.lightTheme i{
        color:white;
    }
}
</style>
