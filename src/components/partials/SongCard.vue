<template>
    <div id="contenitore">
        <img :src="song.poster" :alt="song.ganze">
        <div>{{song.title}}</div>
        <div>{{song.author}}</div>
        <div>{{song.year}}</div>
    </div>
</template>

<script>
    export default {
        name: "SongCard",
        props: ["song"]
    }
</script>

<style lang="scss" scoped>
    #contenitore{
        img{
           width: 100%; 
        }

        color: #fff;
    }
</style>