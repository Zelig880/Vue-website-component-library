<template>
    <div id="o-speakers-banner" v-show="$vuetify.breakpoint.mdAndUp">
        <div id="nameContainer">

            <h2 v-for="(speaker, index) in speakers" 
                :key="index" 
                @click="$vuetify.goTo(`#speaker-${index}`)"
                class="headline">
                {{ speaker.name }}
            </h2>    
        </div>
        <div id="imageContainer">
            <div 
                v-for="(speaker, index) in speakers" 
                :key="index" 
                class="speaker">
                <div>
                    <img 
                        :src="speaker.image" 
                        :alt="`portrait of ${speaker.name}`" 
                        @click="$vuetify.goTo(`#speaker-${index}`)" />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            speakers:[
                { name: "Dean", image: "https://learningally.org/portals/6/images/spod/Dean_Headshot.jpg"},
                { name: "Frankie Shaw", image: "https://www.thewrap.com/wp-content/uploads/2019/04/Frankie-Shaw-1.jpg"},
                { name: "Simone Cuomo", image: "https://www.dddnorth.co.uk/images/profiles/3e104d75-11e5-4a43-ae25-b94a24f7743f_212e1b4.jpg"},

            ]
        }
    }
}
</script>


<style lang="scss">
#o-speakers-banner{
    padding:100px 0px;
}
#nameContainer, #imageContainer{
  width:900px;
  display: flex;
  margin: 0  auto 25px auto;
  justify-content:space-around;
}

#imageContainer{
  justify-content:center;

  .speaker{
        overflow: hidden;
        height:400px;
        border-left: white 10px solid;
        transform: skew(-10deg, 0deg);
    }

    .speaker{
        margin-left:50px;
        margin-left:-75px;
        flex: 1 1 0;
    }

    .speaker div{
        height:100%;
        transform: skew(10deg, 0deg);
    }

    .speaker div img{
        width:100%;
        transform: scale(1.25);
        transition: filter 1s;

        &:hover{
            filter: grayscale(1);
            cursor: pointer;
        }
    }
}


</style>
