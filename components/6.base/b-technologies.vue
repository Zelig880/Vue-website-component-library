<template>
    <div class="b-technologies">
        <i :class="iconName"></i>
    </div>
</template>

<script>
export default {
    props:{
        name:{
            type: String,
            required: true
        }
    },
    computed:{
        iconName(){
            return `fab fa-${this.name}`
        }
    }
}
</script>

<style lang="scss" >
@import '../scss/variable/theme.scss';

.b-technologies{
    
    width:40px;
    height: 40px;
    background-color: $color8;
    border-radius: 4px;
    padding:5px;
    text-align: center;
    
    i{
        font-size:30px;
        color:white;
        width:30px;
        height:30px;
    }
}
</style>
