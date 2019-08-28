<template>
    <div id="s-header">
        <div class="logo">
            <h1>
                <a href="/">
                    <img src="../assets/thisdot-logo.svg" alt="This Dot Logo" />
                </a>
            </h1>
        </div>
        <o-navbar class="navbar"></o-navbar>
        <div class="social">
            <b-social name="facebook" href="https://www.facebook.com/thisdot"></b-social>
            <b-social name="twitter" href="https://twitter.com/thisdotmedia"></b-social>
            <b-social name="youTube" href="https://www.youtube.com/thisdotmedia"></b-social>
            <b-social name="medium" href="https://medium.com/@thisdotmedia"></b-social>
            <b-social name="devto" href="https://dev.to/thisdotmedia_staff"></b-social>
        </div>
    </div>
</template>

<script>
import navbar from "@/4.objects/o-navbar";
import social from "@/6.base/b-social";

export default {
    components: {
      'o-navbar': navbar,
      'b-social': social,
    }
}
</script>

<style lang="scss" scoped>
@import '../scss/variable/theme.scss';

#s-header{
    background-color: $color7;
    display: flex;
    align-content:center;
    justify-content:space-around;
    align-items:center;
    flex-wrap: wrap;

    h1{ //required for screen readers
        font-size:1px;
    }

    img{
        height:25px;
    }

    .navbar{
        align-self: flex-end;
        flex-grow: 0;
        
        @media only screen and (max-width: 960px) {
            padding-bottom: 0px;
            padding-top: 10px;
            display: flex;
        }
    }

    .social{
        display: flex;
        justify-content:space-around;
    }
    
}
</style>
