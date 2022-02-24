<template>
    <div id="container">
        <div class="row">
            <div class="col">
                <LogoVerde/>
            </div>
            <div class="col d-flex align-items-center justify-content-end me-5">
                <form>
                    <select class="mx-2" name="genres" v-model="genreSelected" @change="filtraGeneri()">

                        <option value="">Scegli un genere</option>
                        <option 
                            v-for="(genre, index) in genres" 
                            :key="index" 
                            :value="genre">
                            
                        {{genre}}</option>
                    </select>

                    <select class="mx-2" name="authors" v-model="authorSelected" @change="filtraAutori()">

                        <option value="">Scegli un autore</option>
                        <option 
                            v-for="(author, index) in authors" 
                            :key="index" 
                            :value="author">
                            
                        {{author}}</option>
                    </select>
                </form>
            </div>
        </div>
       
       
    </div>
</template>

<script>

    import LogoVerde from "./partials/LogoVerde.vue"

    export default {
        name:"MyHeader",
        components:{
            LogoVerde,
        },
        props: ["genres", "authors"],
        data(){
          return{
              genreSelected: "",
              authorSelected: ""
          }  
        },
        methods:{
            filtraGeneri(){
                this.$emit("filtraGeneri", this.genreSelected);
            },
            filtraAutori(){
                this.$emit("filtraAutori", this.authorSelected);
            }
        }
    }
</script>

<style lang="scss" scoped>

    @import "./../assets/variables.scss";

    #container{
        background-color: $primaryColor;
        height: 3rem;
    }
</style>