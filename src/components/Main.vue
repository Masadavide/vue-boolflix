<template>
  <div class="container">
    <input type="text">
    <button type="button">Cerca</button>
  </div>
</template>

<script>
import axios from "axios"

export default {
  name: 'Main',
  props: {
    
  },
  data() {
      return {
          
      }
  },
  created(){
      this.getBrani();
  },
  methods: {
      cercaFilm: function(){
        axios
          .get('https://developers.themoviedb.org/3/search/movies', {
            params: {
              api_key: '52964418bdf199e6c4cf74a2f4a59238',
              query: '',
            }
          })
      }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
