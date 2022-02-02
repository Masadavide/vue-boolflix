<template>
<div>
    <input type="text" v-model="valoreText">
    <button type="button"
    @click.prevent="$emit('cerca',valoreText)">Cerca</button>
</div>
</template>

<script>
export default {
    name: "Input",
    data(){
        return{
            valoreText:""
        }
    }
}
</script>

<style>

</style>