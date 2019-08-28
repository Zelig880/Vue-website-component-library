<template>
    <div>  
        <div class="archives-container" v-if="archives.length > 0">
            <template  v-for="(archive, index) in archives">
                <sm-archive-stats v-if="archive.type === 'info'" v-bind="archive" :key="index"/>
                <sm-archive-flipcard v-else :key="index" v-bind="archive" />
            </template>
        </div>
    </div>
</template>

<script>
import flipCard from "@/5.smart/sm-archive-flipcard.vue";
import stats from "@/5.smart/sm-archive-stats.vue";

export default {
    props:{
        archives:{
            type:Array
        }
    },
    components:{
        "sm-archive-stats": stats,
        "sm-archive-flipcard": flipCard
    }
};
</script>

<style lang="scss">
@import "../scss/variable/theme.scss";

.archives-container{
    display:flex;
    flex-wrap: wrap;
    justify-content: space-around;

    & > div{
        margin-bottom: 10px;
    }
}

</style>
