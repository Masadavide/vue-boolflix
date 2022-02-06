<template>
    <header>
        <div class="container">
            <div class="title">
                Boolflix
            </div>
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
        height: 150px;
        
        .title{
            font-size: 40px;
            line-height: 150px;
            text-transform: uppercase;
            display: inline-block;
        }
    }
}
</style>