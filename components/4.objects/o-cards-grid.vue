<template>
    <div>  
        <h2>Previous Speakers..</h2>
        <div class="mini-cards-container">
            <div class="mini=card">
                <img src="../assets/avatar1.jpg" class="speaker" alt="speaker1" />
                <img src="../assets/react.png" class="technology" alt="speaker1" />
                <img src="../assets/vue.png" class="technology" alt="speaker1" />
            </div>
            <div class="mini=card">
                <img src="../assets/avatar1.jpg" class="speaker" alt="speaker1" />
                <img src="../assets/react.png" class="technology" alt="speaker1" />
                <img src="../assets/vue.png" class="technology" alt="speaker1" />
            </div>
            <div class="mini=card">
                <img src="../assets/avatar1.jpg" class="speaker" alt="speaker1" />
                <img src="../assets/react.png" class="technology" alt="speaker1" />
                <img src="../assets/vue.png" class="technology" alt="speaker1" />
            </div>
            <div class="mini=card">
                <img src="../assets/avatar1.jpg" class="speaker" alt="speaker1" />
                <img src="../assets/react.png" class="technology" alt="speaker1" />
                <img src="../assets/vue.png" class="technology" alt="speaker1" />
            </div>
            <div class="mini=card">
                <img src="../assets/avatar1.jpg" class="speaker" alt="speaker1" />
                <img src="../assets/react.png" class="technology" alt="speaker1" />
                <img src="../assets/vue.png" class="technology" alt="speaker1" />
            </div>
        </div>
    </div>
</template>

<script>
export default {
  computed: {
  },
};
</script>

<style lang="scss">
.mini-cards-container{
    display:grid;
    grid-template-columns: auto auto auto auto;

    .speaker{
        width: 100px;
        margin: 15px 10px;
    }

    .technology{
        width: 35px;
    }

}

</style>
