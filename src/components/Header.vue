<template>
    <div class="container">
        <Searchbar @cerca="passaggioDatiSH"/>
    </div>
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

<style>

</style>