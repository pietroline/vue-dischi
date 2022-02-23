<template>
  <div id="app">

    <header>
      <MyHeader/>
    </header>

    <main>
      <MainAlbum/>
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
    }
  }

</script>

<style lang="scss">

</style>
