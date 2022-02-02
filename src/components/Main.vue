<template>
  <div class="container">
    <Input @cerca="filtra"/>
  </div>
</template>

<script>
import axios from "axios"
import Input from "./commons/Input.vue"


export default {
  name: 'Main',
  components:{
    Input
  },
  data() {
      return {
          apiURL:"https://api.themoviedb.org/3/search/movie",
          arrayFilm:[],
          inputText:""
      }
  },
  created(){
      
  },
  methods: {
      getFilm: function(){
        axios
          .get(this.apiURL, {
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
      filtra(value){
        this.inputText = value 
        this.getFilm()
      }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
