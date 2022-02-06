<template>
<main>
  <div class="container">
    <div class="title" v-if="arrayFilm.length != 0">Film</div>
    <div class="container2">
      <Film v-for="(element) in arrayFilm" :key="element.id" :film="element"/>
    </div>
    <div class="title" v-if="arraySerie.length != 0 ">Serie</div>
    <div class="container2">
      <Serie v-for="(element2) in arraySerie" :key="element2.id" :serie="element2"/>
    </div>
  </div>
</main>
</template>

<script>
import Film from "./commons/Film.vue"
import Serie from "./commons/Serie.vue"


export default {
  name: 'Main',
  components:{
    Film,
    Serie
  },
  props:{
    arrayFilm: Array,
    arraySerie: Array
  },
}
</script>

<style scoped lang="scss">
main{
  background-color: #434343;
  width: 100vw;
  height: calc(100vh - 150px);
  overflow-y: scroll;

  .container{

    .title{
      font-size: 50px;
      font-weight: bold;
      color: white;
      text-align: center;
    }

    .container2{
      display: flex;
      flex-wrap: wrap;
      margin: 20px;
    }
  }

}
</style>
