<template>
<div class='user'>
    <header><h1>{{title}}<br>
    <button v-on:click="eventup">change-data-from-son</button>
    </h1></header></div>
</template>
<script>
export default {
    name:'com-header',
    data(){
        return{
        }
    },
    props:{
        title:String

    },
    methods:{
        eventup(e){
            console.log("gửi event up cho cha");
            var data={
                title:"thay đổi dự liệu từ component con thành công"

            }
            this.$emit('changetitle',data)
        }

    }
    
}
</script>
<style>

</style>