<template>
    <div>
        <ul>
            <li class="poster"><img :src="getPoster()" alt=""></li>
            <li>Titolo:{{serie.name}}</li>
            <li>Titolo originale:{{serie.original_name}}</li>
            <li class="flag">Lingua:<img :src="bandiera()" alt=""> </li>
            <li>Voto:{{serie.vote_average}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "Serie",
    props:{
        serie: Object
    },
    methods:{
        bandiera() {
            if(this.serie.original_language == "it"){
                return require("../../assets/img/italy.png")
            }else if(this.serie.original_language == "en"){
                return require("../../assets/img/united-kingdom.png")
            }else{
                return require("../../assets/img/planet-earth.png")
            }
        },
        getPoster(){
            if(this.serie.poster_path != null){
                return  "https://image.tmdb.org/t/p/original" + this.serie.poster_path
            }else{
                return "https://www.goodworking.it/wp-content/uploads/2018/03/pagina-errore-404.jpg"
            }
        }
    }
}
</script>

<style scoped lang="scss">
.poster{
    width: 200px;
    height: 300px;
}
.flag{
    width: 10px;
    height: 15px;
}
img{
    width: 100%;
    height: 100%;
}
</style>