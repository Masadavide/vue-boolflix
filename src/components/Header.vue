<template>
    <header>
        <div class="container">
            Boolflix
            <Searchbar @cerca="passaggioDatiSH"/>
        </div>
    </header>
</template>

<script>
import Searchbar from './commons/Searchbar.vue'
export default {
    components: {
        Searchbar 
    },
    methods:{
        passaggioDatiSH(input){
            this.$emit("evento",input)
        }
    }
}
</script>

<style scoped lang="scss">
header{
    background-color: black;
    color: red;

    .container{
        max-width: 1200px;
        height: 100px;
    }
}
</style>