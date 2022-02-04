<template>
  <div class="container">
    <div class="titolo-film" v-if="arrayFilm.length != 0">Film</div>
    <Film v-for="(element) in arrayFilm" :key="element.id" :film="element"/>
    <div class="titolo-serie" v-if="arraySerie.length != 0 ">Serie</div>
    <Serie v-for="(element2) in arraySerie" :key="element2.id" :serie="element2"/>
  </div>
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

</style>
