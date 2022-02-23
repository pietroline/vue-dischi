<template>
    <div id="container" class="d-flex align-items-center">

       <div class="row row-cols-5">
           <div class="col" v-for="(song, index) in songs" :key="index">
                <SongCard :song="song"/>
           </div>
       </div>

    </div>
</template>

<script>

    //integro axios nel progetto partendo dalla copia presente in node_modules
    const axios = require('axios');

    import SongCard from "./partials/SongCard.vue";

    export default {
        name: "MainAlbum",
        components:{
            SongCard,
        },
        mounted(){
            this.getInfoSongs();
        },
        data(){
            return{
                songs: [],
                endPoint: "https://flynn.boolean.careers/exercises/api/array/music",
            }
        },
        methods: {

            getInfoSongs(){
                axios.get(this.endPoint)
                    .then(response => {
                        this.songs = response.data.response;
                    })
                    .catch(function (error) {
                        console.log(error);
                    })
            }

        }
    }
</script>

<style lang="scss" scoped>

    @import "./../assets/variables.scss";

    #container{
        height: calc(100vh - 3rem);
        background-color: $secondaryColor;

        .row{
            width: 60%;
            margin: 0 auto;
        }
    }
</style>