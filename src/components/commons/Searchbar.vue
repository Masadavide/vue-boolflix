<template>
<div class="searchbar">
    <input type="text" v-model.trim="valoreText">
    <button type="button"
    @click.prevent="$emit('cerca',valoreText)">Cerca</button>
</div>
</template>

<script>
export default {
    name: "Searchbar",
    data(){
        return{
            valoreText:""
        }
    }
}
</script>

<style>
.searchbar{
    float: right;
    line-height: 150px;
}
</style>