<template>
  <div class="component-tab">
       <div class="tab-title">
        <span>{{title}}</span>
       <i class="icon ion-md-heart"></i>
       </div>
       <div class="tab-content">
           <slot></slot>
       </div>

  </div>
</template>
<script>
export default {
  name: "component-tab",
  data() {
    return {};
  },
  props:{
        title:{
            type:String,
            default:'title mac dinh'
    }
  }
};
</script>
<style>
.tab-title{
    border:2px solid black;
    padding: 15px 30px;
    display: flex;
    justify-content: space-between;
}
.list-tab{
    margin: 0;
    padding: 0;
    display: flex;
    list-style: none;
}
.tab-content{
    border: 1px solid green;
    margin: 2px;
    padding: 2px;
}
.list-tab li{
    padding: 8px 15px;
    background-color: #cccccc;
}
.list-tab li:hover{
    background-color: red;
    border:1px solid black;
    cursor: pointer;
    color:blanchedalmond;
    transition: all 2s ease;
}
.active{
  background-color: yellow;
}
</style>