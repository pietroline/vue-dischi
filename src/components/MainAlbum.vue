<template>
    <div id="container" >

        <div v-if="loadingProgress">
          <loadingPage/>
        </div>
        <div v-else>
            <div class="row row-cols-5">
                <div class="col " v-for="(song, index) in filterSongs" :key="index">
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
        props: ["genereSelezionato", "autoreSelezionato"],
        computed:{
            filterSongs(){

                if(this.genereSelezionato != ""){

                    this.resetAuthorArray();

                    //popolo array author con i diversi autori musicali presenti
                    this.songs.forEach(element => {
                        if(!this.authorArray.includes(element.author) && element.genre == this.genereSelezionato){
                            this.authorArray.push(element.author);
                        }
                    });
                    this.$emit("autoriMusicali", this.authorArray);
                    
                    if(this.autoreSelezionato != ""){
                        return this.songs.filter(item =>{
                            return item.author == this.autoreSelezionato;
                            
                        });
                    }else{
                        return this.songs.filter(item =>{
                            return item.genre == this.genereSelezionato;
                            
                        });
                    }
                    
                }else if(this.autoreSelezionato != ""){

                    this.resetGenreArray();
                    
                    //popolo array genre con i diversi generi musicali presenti
                    this.songs.forEach(element => {
                        if(!this.genreArray.includes(element.genre) && element.author == this.autoreSelezionato){
                            this.genreArray.push(element.genre);
                        }
                    });
                    this.$emit("generiMusicali", this.genreArray);

                    return this.songs.filter(item =>{
                        return item.author == this.autoreSelezionato;
                    });

                }else{

                    this.resetAuthorArray();
                    this.resetGenreArray();

                    //popolo array genre con i diversi generi musicali presenti
                    this.songs.forEach(element => {
                        if(!this.genreArray.includes(element.genre)){
                            this.genreArray.push(element.genre);
                        }
                    });
                    this.$emit("generiMusicali", this.genreArray);

                    //popolo array author con i diversi autori musicali presenti
                    this.songs.forEach(element => {
                        if(!this.authorArray.includes(element.author)){
                            this.authorArray.push(element.author);
                        }
                    });
                    this.$emit("autoriMusicali", this.authorArray);

                    return this.songs;
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
                authorArray: [],
                loadingProgress: true,
                endPoint: "https://flynn.boolean.careers/exercises/api/array/music",
            }
        },
        methods: {

            resetAuthorArray(){
                this.authorArray=[];
            },
            resetGenreArray(){
                this.genreArray=[];
            },

            getInfoSongs(){
                axios.get(this.endPoint)
                    .then(response => {
                        this.songs = response.data.response;
                        this.loadingProgress = false;

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
        padding: 5rem;

        .row{
            width: 60%;
            margin: 0 auto;
        }
    }
</style>