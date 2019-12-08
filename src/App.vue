<template>
  <div class="wrapper clearfix">
    <PlayerDuo
      v-bind:scorePlayer="scorePlayer"
      v-bind:currentScore="currentScore"
      v-bind:activePlayer="activePlayer"
      v-bind:isWinner="isWinner"
      v-bind:finalScore="finalScore"
    />
    <Play
      v-on:handlenewgame="handlenewgame"
      v-on:rolldice="rolldice"
      v-on:end="end"
      v-bind:finalScore="finalScore"
      v-on:changefinalscore="changefinalscore"
      v-bind:isPlay="isPlay"
    />
    <dice v-bind:dices="dices" />
    <rules v-on:understand="understand" v-bind:isvisiblerule="isvisiblerule" />

  </div>
  <!--<div id="app">
    <div class="container">
      <homehead v-bind:title="title"
      v-on:changetitle="changetitlefromson"
       />
      <img src="./assets/logo.png" />
      <listuser 
       v-bind:listUser="listUser"
      v-on:chuyengiaotwo="chuyentieptwo"/>
      <homefoot v-bind:title="title"/>
      <demoref />
      <demoSlot />
      
    </div>
  </div>
  -->
</template>

<script>
/**  
import homehead from "./component/homehead.vue";
import listuser from "./component/listuser.vue";
import homefoot from "./component/homefoot.vue";
import demoref from "./component/demoref.vue";
import demoSlot from "./component/demoSlot.vue";
*/
import calculator from "./component/calculator";
import PlayerDuo from "./component/PlayerDuo";
import Play from "./component/Play";
import dice from "./component/dice";
import rules from "./component/rules";
export default {
  name: "app",
  data() {
    return {
      /**  title: "kkk this is my love",
      listUser: [
        { id: 1, email: "1@gmail.com", active: true },
        { id: 2, email: "2@gmail.com", active: false },
        { id: 3, email: "3@gmail.com", active: true },
        { id: 4, email: "4@gmail.com", active: false },
        { id: 5, email: "5@gmail.com", active: true },
        { id: 6, email: "6@gmail.com", active: false }
      ]*/
      scorePlayer: [0, 0],
      currentScore: 90,
      activePlayer: 1,
      isPlay: false,
      isvisiblerule: false,
      dices: [4, 3],
      finalScore: 100
    };
  },
  components: {
    /*   homehead,
    homefoot,
    listuser,
    demoref,
demoSlot*/
    PlayerDuo,
    Play,
    dice,
    rules,calculator
  },
  computed: {
    isWinner() {
      if (this.activePlayer == 1&&this.isPlay==false) {
        if (this.scorePlayer[0] < 22 && this.scorePlayer[1] < 22) {
          if (this.scorePlayer[0] > this.scorePlayer[1]) {
            return 0;
          }
          else if (this.scorePlayer[1] > this.scorePlayer[0]) {
            return 1;
          }
        } else if (this.scorePlayer[0] > 22 && this.scorePlayer[1] < 22) {
          return 1;
        } else if (this.scorePlayer[1] > 22 && this.scorePlayer[0] < 22) {
          return 0;
        }
        else if(this.scorePlayer[0]==0)
        return 1;
        else if(this.scorePlayer[1]==0)
        return 0;
        
      }
      else if(this.activePlayer == 0 && this.isPlay==false){
        return 1;
      }
      return 2;
    }
  },
  methods: {
    changefinalscore(e) {
      var number = e.target.value;
      if (isNaN(parseInt(number))) {
        this.finalScore = "";
      } else {
        this.finalScore = number;
      }
    },
    handlenewgame() {
      this.isvisiblerule = true;
    },
    nextplayer() {
      this.activePlayer = this.activePlayer === 0 ? 1 : 0;
    },
    understand() {
      this.isPlay = true;
      this.isvisiblerule = false;
      this.activePlayer = 0;
      this.scorePlayer = [0, 0];
      this.currentScore = 0;
      this.dices = [1, 1];
    },
    rolldice() {
      if (this.isPlay == true) {
        var dice1 = Math.floor(Math.random() * 6) + 1;
        var dice2 = Math.floor(Math.random() * 6) + 1;
        this.dices = [dice1, dice2];
        this.currentScore += dice1 + dice2;
        if (this.currentScore > 21) {
         /* setTimeout(() => {
            alert("you are a loser");
            this.isPlay = false;
            return;

          }, 10);*/
          this.currentScore = 0;
          this.isPlay = false;

        }
      } else {
        alert("click new game,please!");
      }
    },
    end() {
      if (this.isPlay == true) {
        let { scorePlayer, activePlayer, currentScore } = this;
        let oldscore = scorePlayer[activePlayer];
        let clonescore = [...scorePlayer];
        clonescore[activePlayer] = oldscore + currentScore;
        this.scorePlayer = clonescore;
        // this.$set(this.scorePlayer,activePlayer,oldscore+currentScore)
        this.currentScore = 0;
        if (this.activePlayer == 0) {
          this.nextplayer();
        } else if (this.activePlayer == 1) {
          this.isPlay = false;
        
        }
      } else {
        alert("click new game,please!");
      }
      /*  changetitlefromson(data){
      this.title=data.title;
      console.log("đã nhận event up từ con")
    },
    chuyentieptwo(data){
      console.log("nhan event dot 2",data);
      var indexdel = -1;
      this.listUser.forEach((usr,idx)=>{
        if(usr.id===data.id){
          indexdel=idx;
        }

      });
      if(indexdel!=-1){
        this.listUser.splice(indexdel,1);
      }
    }*/
    }
  }
};
</script>

<style>
/*#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container {
  max-width: 1170px;
  margin: 0 auto;
  padding: 0 15px;
  min-height: 3000px;
}*/
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.clearfix::after {
  content: "";
  display: table;
  clear: both;
}

body {
  background-image: linear-gradient(
      rgba(62, 20, 20, 0.4),
      rgba(62, 20, 20, 0.4)
    ),
    url("/public/images/back.jpg");
  background-size: cover;
  background-position: center;
  font-family: Lato;
  font-weight: 300;
  position: relative;
  height: 100vh;
  color: #555;
}

.wrapper {
  width: 1000px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: #fff;
  box-shadow: 0px 10px 50px rgba(0, 0, 0, 0.3);
  overflow: hidden;
}

</style>
