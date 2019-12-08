<template>
    <div class="list-user">
        <user v-on:chuyengiao="chuyentiep" v-for="user in listUser" v-bind:key="user.id" v-bind:user="user"/>
        
    </div>
</template>
<script>
import user from './user.vue'
export default {
    name:'list-user',
    data(){
        return{
            
        }
    },
    props:{
        listUser:{
            type:Array,
            default:[]
        }

    },
    components:{
        user,
    },
    methods:{
        chuyentiep(data){
            console.log('nhan event dot 1!',data);
            console.log('da truyen event dot 2');
            this.$emit('chuyengiaotwo',data);
            
        }
    }
    
}
</script>
<style>
.list-user{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}
.list-user .user{
    padding: 30px;
    margin-bottom: 30px;
    border:1px solid black;
    width: calc(33.3333%-20px);
}

</style>