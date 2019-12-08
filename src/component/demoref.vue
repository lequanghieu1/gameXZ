<template>
  <div class="demoref">
    <h1>Demoref</h1>
    <button 
    v-on:onclick="inputfile"
    class="avatar">Thay đổi avatar</button>
    <input 
    ref="fileInputAva"
    type="file" style="display:none">
  </div>
</template>
<script>
export default {
  name: "demoref",
  data() {
    return {

    }

  },
  methods:{
    inputfile(e){
      this.$refs.fileInputAva.click();
      //console.log();

    }
  }
};
</script>
<style>
.demoref{
  margin-top: 100px;
  padding:100px 30px;
  border:1px solid gray; 
}
.avatar{
  color:#fff;
  border: 2px solid #333;
  padding: 12px 15px;
  background-color: red;
  transition: all .3s ease; 
}
.avatar:hover{
  background-color: green;
  color:yellow;
}
</style>