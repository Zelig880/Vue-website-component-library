<template>
    <div class="sm-archive-stats">
        <p class="value xx-large">{{ value }} </p>
        <p class="medium">{{ content }}</p>
    </div>
</template>

<script>
export default {
    props:{
        title:{
            type: String,
            required: true,
            default: "Archive"
        },
        content:{
            type: String,
            required: true
        },
        value:{
            type: String
        }
    },
    computed: {
    }
}
</script>

<style lang="scss">
@import "../scss/variable/theme.scss";


.sm-archive-stats{
    flex:0 0 256px;
    text-align: center;
    padding-top:50px;
    height: 322px;
    margin:14px 16px;
    background-color: $color11;
    border-radius: 4px;

    p{
        font-weight: bolder;
        padding-left:15px;
        padding-right:15px;
        color:white;
        font-weight: 500;

        &.value{
            font-weight: bold;
            color:$color13;
        }
    }
}
</style>
