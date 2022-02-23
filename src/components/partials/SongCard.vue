<template>
    <div id="contenitore">
        
        <a href="#" class="card my-2">

            <div class="d-flex justify-content-center">
                <img class="w-75 py-3" :src="song.poster" :alt="song.ganze">
            </div>
            
            <div class="card-body text-center">
                <h1 class="fs-5">{{song.title}}</h1>
                <div class="text_grey">{{song.author}}</div>
                <div class="text_grey">{{song.year}}</div>
            </div>
        </a>

    </div>
</template>

<script>
    export default {
        name: "SongCard",
        props: ["song"]
    }
</script>

<style lang="scss" scoped>

    @import "./../../assets/variables.scss";

    #contenitore{

        a{
            text-decoration: none;
        }

        .card{
            background-color: $primaryColor;
            color: #fff;

            height: 22rem;

            text-transform: uppercase;

            .text_grey{
                color: $greyText;
            }
        }
    
    }
</style>