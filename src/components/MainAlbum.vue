<template>
    <div id="container" class="d-flex align-items-center justify-content-center">

        <div v-if="loadingProgress">
          <loadingPage/>
        </div>
        <div v-else>
            <div class="row row-cols-5">
                <div class="col" v-for="(song, index) in filterSongs" :key="index">
                    <SongCard :song="song"/>
                </div>
            </div>
        </div>

    </div>
</template>

<script>

    //integro axios nel progetto partendo dalla copia presente in node_modules
    const axios = require('axios');

    import SongCard from "./partials/SongCard.vue";
    import LoadingPage from "./partials/LoadingPage.vue"

    export default {
        name: "MainAlbum",
        components:{
            SongCard,
            LoadingPage,
        },
        props: ["genereSelezionato"],
        computed:{
            filterSongs(){

                if(this.genereSelezionato == ""){
                    return this.songs;
                }else{
                    return this.songs.filter(item =>{
                        return item.genre == this.genereSelezionato;
                        
                    });
                }
            }
        },
        mounted(){
            this.getInfoSongs();
        },
        data(){
            return{
                songs: [],
                genreArray: [],
                loadingProgress: true,
                endPoint: "https://flynn.boolean.careers/exercises/api/array/music",
            }
        },
        methods: {

            getInfoSongs(){
                axios.get(this.endPoint)
                    .then(response => {
                        this.songs = response.data.response;
                        this.loadingProgress = false;

                        //popolo array genre con i diversi generi musicali presenti
                        this.songs.forEach(element => {
                            if(!this.genreArray.includes(element.genre)){
                                this.genreArray.push(element.genre);
                            }
                        });
                        this.$emit("generiMusicali", this.genreArray);

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