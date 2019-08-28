<template>
    <div id="o-questionnaire-container">
        <div  id="question-1">
            <h3>What technologies interests you?</h3>
            <div class="question" @click="showQuestion2 = true">
                <div class="option">React</div>
                <div class="option">Vue</div>
                <div class="option">Angular</div>
                <div class="option">Vanilla JS</div>
            </div>
        </div>
        <transition name="fade">
            <div id="question-2" 
            v-if="showQuestion2">
                <h3>What media do you prefer?</h3>
                <div class="question" @click="showArchive = true">
                    <div class="option">Podcast</div>
                    <div class="option">YouTube meetings</div>
                    <div class="option">Blog Post</div>
                    <div class="option">Tutorial</div>
                </div>
            </div>
        </transition>
        <sm-archive  
            v-if="showArchive"
            v-bind="archive"
            class="archive"/>
    </div>
</template>

<script>
import archive from "@/5.smart/sm-archive.vue";

export default {
    data(){
        return {
            showArchive: false,
            showQuestion2: false,
            archive: {
                  title: "React advanced and more",
                  technologyImage: "/img/tech/react.png",
                  speakers:[
                      { name: "Simone Cuomo", image: "/img/speakers/avatar1.jpg"},
                      { name: "Simone Cuomo", image: "/img/speakers/avatar1.jpg"}
                  ]
            }
        }
    },
    methods:{
        showQuestion(questionNumber){
            this.$el.querySelector("#question-2").classList.remove("hidden");
        }
    },
    components:{
        "sm-archive": archive
    }
}
</script>

<style lang="scss" scoped>
@import "../scss/variable/theme.scss";
.fade-enter-active, .fade-leave-active {
  transition: opacity 2s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

#o-questionnaire-container{
    
    text-align: center;

    .question{
        width:100%;
        display: flex;
        justify-content: space-evenly;
        margin-bottom: 50px;

        .option{
            flex-grow:1;
            height:50px;
            background-color: $color4;
            padding: 15px 10px 5px 10px;
            margin:5px 10px;
            border-radius: 5px;
            box-shadow: 5px 5px 10px $color8;
            vertical-align: center;
            font-weight: bold;
            cursor: pointer;
            text-align: center;

            &:hover{
                background-color: $color1;
            }
        }
    }

    .archive{
        width:50%;
        margin: 0 auto;
    }
}
</style>
