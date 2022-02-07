<template>
    <div class="container">
        <div class="poster" @mouseover="show = true"   @mouseleave="show = false">
            <img :src="getPoster()" alt="" v-if="!show">
            <ul v-if="show">
                <div class="text">
                    <li>Titolo:
                        <span class="lowercase">
                        {{serie.name}}
                        </span>
                    </li>
                    <li>Titolo originale:
                        <span class="lowercase">
                            {{serie.original_name}}
                        </span> 
                    </li>
                    <li class="flag">Lingua:
                        <img :src="getBandiera(this.serie.original_language)" alt=""> 
                    </li>
                    <li>Voto:
                        <span class="stella" v-for="element in getStar(vote)" :key="element.id">
                            <i class="fas fa-star"></i>
                        </span>
                        <span class="stella" v-for="element2 in (5-getStar(vote))" :key="element2.id">
                            <i class="far fa-star"></i>
                        </span>
                    </li>
                    <li>Panoramica:
                        <span class="lowercase">
                            {{serie.overview}}
                        </span>
                    </li>
                </div>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: "Serie",
    data(){
        return{
            show: false,
            vote: ""
        };
    },
    props:{
        serie: Object
    },
    methods:{
        getBandiera(language) {
            if(language == "it"){
                return require("../../assets/img/italy.png")
            }else if(language == "en"){
                return require("../../assets/img/united-kingdom.png")
            }else{
                return require("../../assets/img/international.png")
            }
        },
        getPoster(){
            if(this.serie.poster_path != null){
                return  "https://image.tmdb.org/t/p/original" + this.serie.poster_path
            }else{
                return "https://www.goodworking.it/wp-content/uploads/2018/03/pagina-errore-404.jpg"
            }
        },
        getStar(){
            this.vote = Math.ceil(this.serie.vote_average / 2)
            return this.vote
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