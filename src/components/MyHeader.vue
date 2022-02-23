<template>
    <div id="container">
       <LogoVerde/>
    </div>
</template>

<script>

    import LogoVerde from "./partials/LogoVerde.vue"

    export default {
        name:"MyHeader",
        components:{
            LogoVerde,
        }
    }
</script>

<style lang="scss" scoped>

    @import "./../assets/variables.scss";

    #container{
        background-color: $headerColor;
        height: 3rem;
    }
</style>