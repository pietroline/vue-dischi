<template>
    <div id="container">
        <div class="row">
            <div class="col">
                <LogoVerde/>
            </div>
            <div class="col d-flex align-items-center justify-content-end me-5">
                <form>
                    <select name="" v-model="selected" @change="filtraGeneri()">

                        <option value="">Scegli un genere</option>
                        <option 
                            v-for="(genre, index) in genres" 
                            :key="index" 
                            :value="genre">
                            
                        {{genre}}</option>

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
        props: ["genres"],
        data(){
          return{
              selected: ""
          }  
        },
        methods:{
            filtraGeneri(){
                this.$emit("filtraGeneri", this.selected);
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