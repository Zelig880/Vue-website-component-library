<template>
  <div >
    <o-full-banner 
      v-if="talkInfo" 
      v-bind="talkInfo" 
      :speakers="speakers">
    </o-full-banner>

    <h2 class="text-center" id="speakers">Speakers</h2>
    <o-speaker-info 
      v-for="(speaker, index) in speakers" 
      :key="index"
      :id="`speaker-${index}`" 
      v-bind="speaker"
      :reverseFlexDirection="index % 2 == 0">
    </o-speaker-info>

    <h2 v-if="archives.length !== 0" class="text-center" id="archive">Archive</h2>
    <o-archives :archives="archives"></o-archives>

    <o-newsletter></o-newsletter>
  </div>
</template>

<script>
import archives from "@/4.objects/o-archives";
import fullBanner from "@/4.objects/o-full-banner";
import speakerInfo from "@/4.objects/o-speaker-info";
import newsletter from "@/4.objects/o-newsletter";
import dataLoaderMixin from "@/mixins/dataLoader-mixin";


export default {
    data(){
      return{
        speakers:[],
        talkInfo:null,
        archives: []
      }
    },
    components: {
      'o-archives': archives,
      'o-newsletter': newsletter,
      'o-full-banner': fullBanner,
      'o-speaker-info':speakerInfo
    },
    mounted(){
      const currentEvent = this.fetchData("currentEvent");
      this.archives = this.fetchData("archive");
      this.speakers = currentEvent.speakers;
      this.talkInfo = currentEvent.talkInfo;
    },
    mixins:[dataLoaderMixin]
}
</script>

<style lang="scss">

@import "../scss/variable/theme.scss";

</style>

