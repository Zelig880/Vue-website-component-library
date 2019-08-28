<template>
    <div id="footer">
        <div class="footer-siteMap">
            <div>  
                <h4 class="font_color-light">Vue Meetup</h4>
                <ul class="no-style">
                    <li><a href="/#/cfp">CFP</a></li>
                    <li><a href="/#/privacy">Privacy</a></li>
                    <li><a href="#speakers">Speakers</a></li>
                    <li><a href="#archive">Archive</a></li>
                </ul>
            </div>
            <div>  
                <h4 class="font_color-light">This Dot Labs</h4>
                <ul class="no-style">
                    <li><a href="https://thisdot.co" rel="noopener">Labs</a></li>
                    <li><a href="https://www.vuemeetup.com" rel="noopener">Vue Meetup</a></li>
                    <li><a href="https://www.reactjsmeetup.com" rel="noopener">ReactJs Meetup</a></li>
                    <li><a href="https://www.angularmeetup.com" rel="noopener">Angular Meetup</a></li>
                </ul>
            </div>
        </div>
        <div>
            <div class="social">
                <b-social name="facebook" href="https://www.facebook.com/thisdot" :lightTheme="true"></b-social>
                <b-social name="twitter" href="https://twitter.com/thisdotmedia" :lightTheme="true"></b-social>
                <b-social name="youTube" href="https://www.youtube.com/thisdotmedia" :lightTheme="true"></b-social>
                <b-social name="medium" href="https://medium.com/@thisdotmedia" :lightTheme="true"></b-social>
                <b-social name="devto" href="https://dev.to/thisdotmedia_staff" :lightTheme="true"></b-social>
            </div>
            <p class="font_color-light caption">© 2018 This Dot, Inc. All Rights Reserved</p>
        </div>
    </div>
</template>

<script>
import social from '@/6.base/b-social.vue';

export default {
    components:{
        'b-social': social
    }
}
</script>

<style lang="scss">
@import '../scss/variable/theme1.scss';
@import '../scss/elements/list.scss';

#footer{
    display: grid;
    grid-template-columns: auto 20%;

    .social{
        
        padding:25px;

        a{
            margin:0 5px;
        }
    }

    .footer-siteMap{
        display: flex;
        padding:0 5%;

        & > div{
            flex-grow: 1;
        }

        a{
            text-decoration: none;
            color: $color4;

            &:hover{
                color: rgba( $color4, .7 )
            }
        }

    }
}
</style>
