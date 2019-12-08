<template>
  <div class="rules " v-bind:class="getclassopenrule">
    <div class="rule">
      <h3>Luật chơi tài xỉu</h3>
      <p>
        Điểm số lớn nhất là 21,nếu 1 bên có điểm lớn hơn 21 thì sẽ 
        bị xử thua ngay lập tức,và bên còn lại sẽ thắng,trường hợp 
        2 bên đều nhỏ hơn 21,thì ai cao điểm hơn sẽ thắng,hãy đặt cược trước khi vào trận,
        nếu không sẽ mặc định là 100(nghìn đồng)
      </p>
      <button v-on:click="understand" class="bottom">Đã hiểu</button>
    </div>
  </div>
</template>
<script>
export default {
  name: "rules",
  data() {
    return {};
  },
  props:{
    isvisiblerule:{type:Boolean,default:false}

  },
  methods:{
    understand(){
      this.$emit('understand');
    }

  },
  computed:{
    getclassopenrule(){
     // return {'openrules':this.isvisiblerule}
     if(this.isvisiblerule==true){
       return 'openrules';
     }
    }

  }
};
</script>
<style>
.rules{
    position: fixed;
    top:0;
    right: 0;
    left: 0;
    bottom: 0;
    background-color: rgba(0,0,0,0.4);
    opacity: 0;
    visibility: hidden;
    transition: all 1s ease;
}
.rules.openrules{
  opacity: 1;
  visibility: visible;
}
.rule{
    width: 350px;
    padding: 20px;
    top:50%;
    left: 50%;
    transform: translate(-50% -50%) scale(1.2);   
    background-color: white;
    position: absolute;
    font-family: Arial, Helvetica, sans-serif;
}
.rules h3{
    margin-bottom: 10px;
}
.openrules .rule{
  transform:translate(-50% -50%) scale(2.0);
}
.rules .bottom{
    border :2px solid black;
    background-color: white;
    padding:8px 15px;
    margin-top: 20px;
    cursor: pointer;
}
.rules .bottom:hover{
    color: white;
    background-color: black;
}
</style>