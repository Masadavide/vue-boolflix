<template>
  <div class="container">
    <Searchbar @cerca="filtra"/>
    <div class="titolo-film" v-if="arrayFilm.length != 0">Film</div>
    <Film v-for="(element) in arrayFilm" :key="element.id" :film="element"/>
    <div class="titolo-serie" v-if="arraySerie.length != 0 ">Serie</div>
    <Serie v-for="(element) in arraySerie" :key="element.id" :serie="element"/>
  </div>
</template>

<script>
import axios from "axios"
import Searchbar from "./commons/Searchbar.vue"
import Film from "./commons/Film.vue"
import Serie from "./commons/Serie.vue"


export default {
  name: 'Main',
  components:{
    Searchbar,
    Film,
    Serie
  },
  data() {
      return {
          apiURLfilm:"https://api.themoviedb.org/3/search/movie",
          apiURLserie:"https://api.themoviedb.org/3/search/tv",
          arrayFilm:[],
          arraySerie:[],
          inputText:""
      }
  },
  created(){

  },
  methods: {
    getFilm: function(){
      axios
        .get(this.apiURLfilm, {
          params: {
            api_key: '52964418bdf199e6c4cf74a2f4a59238',
            query: this.inputText,
          }
        })
        .then((risposta) => {
          this.arrayFilm = risposta.data.results;
          console.log(this.arrayFilm)
        })
        .catch(function (error) {
          console.log(error)
        })
      
      axios
        .get(this.apiURLserie, {
          params: {
            api_key: '52964418bdf199e6c4cf74a2f4a59238',
            query: this.inputText,
          }
        })
        .then((risposta) => {
          this.arraySerie = risposta.data.results;
          console.log(this.arraySerie)
        })
        .catch(function (error) {
          console.log(error)
        })
    },
    filtra(value){
      this.inputText = ""
      this.inputText = value 
      this.getFilm()
    },
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
