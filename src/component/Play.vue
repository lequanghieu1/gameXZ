<template>
    <div class="play">
        <button v-on:click="newgame" 
        class="control btn-new"><i class="ion-ios-plus-outline"></i>New game</button>
            <button v-on:click="rolldice"
             class="control btn-roll"><i class="ion-ios-loop"></i>Roll dice</button>
            <button v-on:click="end"
            class="control btn-hold"><i class="ion-ios-download-outline"></i>Hold</button>
            
            <input v-bind:value="finalScore" v-bind:disabled="isPlay"
            v-on:input="$emit('changefinalscore',$event)"
            type="number" placeholder="Final score" class="final-score">
    </div>
</template>
<script>
export default {
    name:'play',
    data(){
        return{

        }
    },
    methods:{
        newgame(){
            this.$emit('handlenewgame');
        },
        rolldice(){
            this.$emit('rolldice')
        },
        end(){
            this.$emit('end')
        }
    },
    props:{
        finalScore:{type:[Number,String],default:100},
        isPlay:{type:Boolean,default:100}

    }
    
    
}
</script>
<style>
.control {
    position: absolute;
    width: 200px;
    left: 50%;
    transform: translateX(-50%);
    color: #555;
    background: none;
    border: none;
    font-family: Lato;
    font-size: 20px;
    text-transform: uppercase;
    cursor: pointer;
    font-weight: 300;
    transition: background-color 0.3s, color 0.3s;
}
.control.disable {
    pointer-events: none;
}

.control:hover { font-weight: 600; }
.control:hover i { margin-right: 20px; }

.control:focus {
    outline: none;
}

.control i {
    color: #42b983;
    display: inline-block;
    margin-right: 15px;
    font-size: 32px;
    line-height: 1;
    vertical-align: text-top;
    margin-top: -4px;
    transition: margin 0.3s;
}

.btn-new { top: 45px;}
.btn-roll { top: 403px;}
.btn-hold { top: 467px;}

.final-score {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    top: 520px;
    color: #555;
    font-size: 18px;
    font-family: 'Lato';
    text-align: center;
    padding: 10px;
    width: 160px;
    text-transform: uppercase;
}

.final-score:focus { outline: none; }

</style>