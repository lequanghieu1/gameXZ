<template>
  <div class="demoSlot">
    <componentab title="Tieu de cua tab">
        <ul class="list-tab">
            <li 
            v-on:click="setActive(index)"
            v-bind:class="{active:tabActive == index}"
            v-for="(item,index) in listab" v-bind:key="index">{{item.text}}</li>
        </ul>
        <div class="tab-content1" v-if="tabActive===0">
            <p>tab 1Lorem ipsum dolor sit amet consectetur adipisicing elit. Assumenda
                 temporibus eius commodi nam dicta. Reiciendis sequi amet hic quibusdam, 
                 vel dolorem error ipsum aut,
                 ullam, odio nesciunt illum exercitationem eos.</p>

        </div>
        <div class="tab-content2" v-if="tabActive===1">
            <p>tab 2Lorem ipsum dolor sit amet consectetur adipisicing elit. Assumenda
                 temporibus eius commodi nam dicta. Reiciendis sequi amet hic quibusdam, 
                 vel dolorem error ipsum aut,
                 ullam, odio nesciunt illum exercitationem eos.</p>
        </div>
        <div class="tab-content3" v-if="tabActive===2">
            <p>tab 3Lorem ipsum dolor sit amet consectetur adipisicing elit. Assumenda
                 temporibus eius commodi nam dicta. Reiciendis sequi amet hic quibusdam, 
                 vel dolorem error ipsum aut,
                 ullam, odio nesciunt illum exercitationem eos.</p>
        </div>
    </componentab>
  </div>
</template>
<script>
import componentab from "./componentab.vue";
export default {
  name: "demoSlot",
  data() {
    return {
      listab: [
          { text: "Tab1" }, 
          { text: "Tab2" }, 
          { text: "Tab3" }],
          tabActive: 1
    }
  },
  components: {
    componentab
  },
  methods:{
    setActive(index){
      this.tabActive = index;
    }
  }
};
</script>
<style>
.demoSlot {
  margin-top: 100px;
  padding: 100px 30px;
  border: 1px solid blue;
}
.active{
  background-color:blue; 
}
</style>