<template>
  <div id="app">

    <header>
      <MyHeader :genres="genres" @filtraGeneri="filter"/>
    </header>

    <main>
      <MainAlbum @generiMusicali="findGenre" :genereSelezionato="genereSelezionato"/>
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
        genereSelezionato: "",
      }
    },
    methods:{
      findGenre(generi){
        this.genres = generi;
      },
      filter(genere){
        this.genereSelezionato = genere;
      }
    }
  }

</script>

<style lang="scss">

</style>
