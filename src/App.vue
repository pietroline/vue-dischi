<template>
  <div id="app">

    <header>
      <MyHeader :genres="genres" :authors="authors" @filtraGeneri="genreFilter" @filtraAutori="authorFilter"/>
    </header>

    <main>
      <MainAlbum @generiMusicali="findGenre" @autoriMusicali="findAuthor" :genereSelezionato="genereSelezionato" :autoreSelezionato="autoreSelezionato"/>
    </main>
  
  </div>
</template>

<script>

  import MyHeader from "./components/MyHeader.vue";
  import MainAlbum from "./components/MainAlbum.vue";


  export default {
    name: 'App',
    components: {
      MyHeader,
      MainAlbum,
    },
    data(){
      return{
        genres: [],
        authors: [],
        genereSelezionato: "",
        autoreSelezionato: "",
      }
    },
    methods:{
      findGenre(generi){
        this.genres = generi;
      },
      findAuthor(autori){
        this.authors = autori;
      },
      genreFilter(genere){
        this.genereSelezionato = genere;
      },
      authorFilter(autore){
        this.autoreSelezionato = autore;
      }
    }
  }

</script>

<style lang="scss">

</style>
