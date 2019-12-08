<template>
    <footer><h1>{{title}}</h1></footer>
</template>
<script>
export default {
    name:'com-footer',
    data(){
        return{
        }
    },
    props:{
        title:{
           type: String,
        default:'This is Footer'
        }

    }
    
}
</script>
<style>

</style>