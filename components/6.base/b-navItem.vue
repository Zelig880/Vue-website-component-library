<template>
    <a class="navItem" :class="{ current: isCurrent }" :href="path" >{{name}}</a>
</template>

<script>
var currentTheme = process.env.VUE_APP_THEME.trim();

export default {
    props:{
        name: String,
        href: {
            type:String,
            required:false,
            default: null
        }
    },
    data(){
        return {
            isCurrent: false
        }
    },
    computed:{
        path(){
            if(!this.href){
                return `/#/${this.name}`;
            }else{
                return this.href;
            }
        }
    },
    mounted(){
        if(this.name.toLocaleLowerCase().indexOf(currentTheme) !== -1){
            this.isCurrent = true;
        }
    }
}
</script>


<style lang="scss">
@import '../scss/variable/theme.scss';

.navItem{
    
    padding: 8px 16px;
    color: $color8;
    font-size: 16px;
    line-height: 1em;
    font-weight: 600;
    text-decoration: none;
    
    &:hover{
        color:rgba( $color8, .8 );
    }

    &:active, &.current{
        color: $color9;
    }
}
</style>

