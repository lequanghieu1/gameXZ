<template>
  <div class="user">
    <p>{{user.email}}</p>
    <button v-on:click="handledel" class="delete">Delete</button>
  </div>
</template>
<script>
export default {
  name: "user",
  data() {
    return {};
  },
  props: {
    user: {
      type: Object,
      default: null
    }
  },
  methods:{
    handledel(e){
       var data={
        id:this.user.id

      }
      console.log('truyen event dot 1 thanh cong');
      this.$emit('chuyengiao',data);
      
    }
  }
};
</script>
<style>
.user{
position: relative;
}
.user .delete{
  position: absolute;
  top:0px;
  right: 0px;
}
</style>