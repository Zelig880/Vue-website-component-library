<template>
    <nav>
        <b-navItem  v-for="(item, index) in navItems"  v-bind="item" :key="index" /> 
    </nav>
</template>

<script>
import navItem from '@/6.base/b-navItem.vue';

export default {
    data() {
        return {
            navItems:[
                {name: "Vue Meetup", href: "https://www.vuemeetup.com"},
                {name: "Angular Meetup", href: "https://www.angularmeetup.com"},
                {name: "React Meetup", href: "https://www.reactjsmeetup.com"}
            ]
        }
    },
    components:{
        'b-navItem': navItem
    }
}
</script>

<style lang="scss">
</style>

