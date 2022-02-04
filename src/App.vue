<template>
  <div id="app">
    <Header @evento="filtra"/>
    <Main :arrayFilm="arrayFilm" :arraySerie="arraySerie"/>
  </div>
</template>

<script>
import axios from "axios"
import Header from "./components/Header.vue"
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return{
      inputText: "",
      apiURLfilm:"https://api.themoviedb.org/3/search/movie",
      apiURLserie:"https://api.themoviedb.org/3/search/tv", 
      arrayFilm:[],
      arraySerie:[],
    }
  },
  props:{

  },
  /* computed:{
    arrayFilmSerie(){
      return [...this.arrayFilm, ...this.arraySerie]
    }
  }, */
  methods:{
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
    },
    getSerie: function(){
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
      this.getSerie()
    },
  }
}
</script>

<style lang="scss">

</style>
