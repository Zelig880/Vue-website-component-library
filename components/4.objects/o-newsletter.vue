<template>
    <div class="o-newsletter">
        <div class="content">
            <div>
                <h2>Subscribe</h2>
                <p>Never miss a meetup again!</p>
                <div class="inputContainer">
                    <v-text-field
                        label="Email Address"
                        prepend-inner-icon="email"
                        v-model="email"
                        :error-messages="emailErrors"
                    ></v-text-field>
                    <button @click="submitMailchimpRequest">SUBSCRIBE</button>
                </div>
            </div>
        </div>
    </div>

</template>

<script>
import lambdaMixin from '../mixins/lambdaFunctionCaller-mixin.js';

export default {
    data(){
        return{
            email: "",
            emailErrors: []
        }
    },
    methods:{
        validateEmail(field, fieldError){
            const emailRegex = /.+@.+\..+/;
            this[fieldError] = [];

            if(this[field].length === 0){ 
                this[fieldError].push("An email is required."); 
                return false;
            }else if(!emailRegex.test(this[field])){
                this[fieldError].push("The email address is not valid."); 
                return false;
            }

            return true;
        },
        submitMailchimpRequest(){
            if(!this.validateEmail("email", "emailErrors")) return;

            var params = {
                "email": this.email,
                "merge_fields": {
                    "Registration_type": "Events Newsletter"
                }
            }

            this.addContactToMailingList(process.env.VUE_APP_MAILCHIMP_NEWSLETTER_LIST_ID, params)

        }
    },
    mixins:[lambdaMixin]
}
</script>

<style lang="scss">
@import "../scss/variable/theme.scss";

.o-newsletter{
    position: relative;
    margin-top:50px;
    margin-left: -50vw;
    left: 50%;
    width: 100vw;
    text-align: center;
    background-color: rgba($color6, 0.5);
    
    height: 500px;

    .content{
        display: flex;
        align-items:center;
        max-width:$site-width;
        margin:0 auto;
        padding:100px 0;

        h2{
            font-size: 48px;
            color:white;
            line-height: 150%;
        }

        & > div{
            max-width: 650px;
            margin: 0 auto;
        }
        
        .inputContainer{
            display: flex;
            padding:10px 15px;
            background-color: white;
            border: 1px solid #A4DEC6;
            border-radius: 4px;
            width: 640px;
            margin:auto;
            
            @media only screen and (max-width: 960px) {
                width: 90%;
                display:flex;
                flex-direction:column;
            }

            button{
                color: $color12;
                font-weight: 600;
                font-size: 20px;
            }
        }
    }
    img{
        margin-right:50px;
    }
}
</style>
