<template>
    <div>
        <ul>
            <li class="poster"><img :src="getPoster()" alt=""></li>
            <li>Titolo:{{film.title}}</li>
            <li>Titolo originale:{{film.original_title}}</li>
            <li class="flag">Lingua:<img :src="getBandiera()" alt=""> </li>
            <li>Voto:{{getStar()}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "Film",
    props:{
        film: Object
    },
    methods:{
        getBandiera() {
            if(this.film.original_language == "it"){
                return require("../../assets/img/italy.png")
            }else if(this.film.original_language == "en"){
                return require("../../assets/img/united-kingdom.png")
            }else{
                return require("../../assets/img/planet-earth.png")
            }
        },
        getPoster(){
            if(this.film.poster_path != null){
                return  "https://image.tmdb.org/t/p/original" + this.film.poster_path
            }else{
                return "https://www.goodworking.it/wp-content/uploads/2018/03/pagina-errore-404.jpg"
            }
        },
        getStar(){
            return (this.film.vote_average / 2).toFixed(0)
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