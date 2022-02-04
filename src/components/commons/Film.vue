<template>
    <div>
        <ul>
            <li class="poster"><img :src="getPoster()" alt=""></li>
            <li>Titolo:{{film.title}}</li>
            <li>Titolo originale:{{film.original_title}}</li>
            <li class="flag">Lingua:
                <img :src="getBandiera(this.film.original_language)" alt=""> 
            </li>
            <li>Voto:
                <div class="stella" v-for="element in getStar()" :key="element.id">
                    <i class="fas fa-star"></i>
                </div>
            </li>
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
        getBandiera(language) {
            if(language == "it"){
                return require("../../assets/img/italy.png")
            }else if(language == "en"){
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
            const stelleArray = [];
            const stelle = (this.film.vote_average / 2)
            for (let i = 0; i < stelle; i++) {
                stelleArray.push(1);
                console.log(stelle +"stelle")
            }
            return  stelleArray
            
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
    display: inline-block;
}
img{
    width: 100%;
    height: 100%;
    display: inline-block;
}
.stella{
    width: 30px;
    height: 30px;
}
</style>