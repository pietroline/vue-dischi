<template>
    <div id="container">
       <div class="row">
           <div class="col">
                <SongCard/>
           </div>
           
       </div>
    </div>
</template>

<script>

    import SongCard from "./partials/SongCard.vue";

    export default {
        name: "MainAlbum",
        components:{
            SongCard,
        },
    }
</script>

<style lang="scss" scoped>

    @import "./../assets/variables.scss";

    #container{
        background-color: $secondaryColor;
        height: calc(100vh - 3rem); // calc(100vh - header hight)
    }
</style>