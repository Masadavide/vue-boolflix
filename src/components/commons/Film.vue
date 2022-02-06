<template>
    <div class="container">
        <div class="poster" @mouseover="show = true"   @mouseleave="show = false">
            <img :src="getPoster()" alt="" v-if="!show">
            <ul v-if="show">
                <div class="text">
                    <li>Titolo:
                        <span class="lowercase">
                        {{film.title}}
                        </span>
                    </li>
                    <li>Titolo originale:
                        <span class="lowercase">
                            {{film.original_title}}
                        </span> 
                    </li>
                    <li class="flag">Lingua:
                        <img :src="getBandiera(this.film.original_language)" alt=""> 
                    </li>
                    <li>Voto:
                        <div class="stella" v-for="element in getStar()" :key="element.id">
                            <i class="fas fa-star"></i>
                        </div>
                    </li>
                    <li>Panoramica:
                        <span class="lowercase">
                            {{film.overview}}
                        </span>
                    </li>
                </div>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: "Film",
    data(){
        return{
            show: false
        };
    },
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
            }
            return  stelleArray
        }
    }
}
</script>

<style scoped lang="scss">
.container{
    .poster::-webkit-scrollbar {
        display: none;
    }
    
    .poster{
        width: 200px;
        height: 300px;
        background-color: black;
        color: white;
        border: 1px solid white;
        margin: 20px 0;
        overflow-y: scroll;

        .text{
            padding: 10px;
        }

        li{
            font-weight: bold;
            font-size: 20px;

            .lowercase{
                font-weight: lighter;
                font-size: 15px;
            }
        }
    
        .flag{
            display: inline-block;

            img{
                width: 10px;
                height: 15px;
                display: inline-block;
                vertical-align: middle;
            }
        }
        img{
            width: 100%;
            height: 100%;
        }
        .stella{
            width: 30px;
            height: 30px;
            display: inline;
            color: gold;
        }
    
    }
}

</style>