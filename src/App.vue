<template>
<div class="whackamole">
    <h1 class="logo">
      Whackamole
    </h1>
    <button
    class='start-game'
    v-on:click='startGame'>
      Start Game
    </button>
    <!-- 固定値はv-bindせずそのまま代入できる-->
    <div class="counters-container">
      <Counter 
        label='Score'
        v-bind:value='score'/>
      <Counter 
        label='HighScore'
        v-bind:value='highScore'/>
      <Counter 
        label='Timer'
        v-bind:value='timer'/>
    </div>
    <!--this.$emitで子から送られきたイベントでv-onでリッスンできる-->
    <Moles 
    v-bind:molesState='moles'
    v-on:whacked='handleWhack'
    v-bind:gameActive='gameActive'/>
  </div>
  
</template>

<script>
import Moles from './components/Moles'
import Counter from './components/Counter'

const molesTimers = [0,0,0,0]
export default {
    name: 'App',
    data: ()=>{
        return{
            score: 0,
            highScore: 20,
            timer: 20,
            moles: [false,false,false,false],
            gameActive: false
        }
    },
    methods:{
        startGame: function(){
            this.startTimer();
            this.score = 0;
            this.timer = 20;
            this.moles = [false,false,false,false]
            this.gameActive = true
            this.startMoles();
        },
        handleWhack: function(moleId){
            this.score++;
        },
        startTimer: function(){
            //setInterval() メソッドは、一定の遅延間隔を置いて関数やコードスニペットを繰り返し呼び出します。
            //これは、インターバルを一意に識別する interval ID を返します。
            this.timerId = setInterval(() => {
                this.decrementSec();
            }, 1000);
        },
        decrementSec: function(){
            this.timer--;
            if(this.timer===0){
                this.stopTimer();
                this.updateScore();
                this.gameActive = false
                this.stopMoles();
            }
        },
        stopTimer: function(){
            //setInterval を使用して設定された繰り返し動作をキャンセルします。
            clearInterval(this.timerId)
        },
        updateScore: function(){
            if(this.score > this.highScore){
                this.highScore = this.score
            }
        },
        startMoles: function(){
            this.molesTimer = setInterval(this.activateMoleRandomly.bind(this),500);
        },
        stopMoles: function(){
            clearInterval(this.molesTimer);
        },
        activateMoleRandomly: function(){
            const index = Math.floor(Math.random() * this.moles.length);
            if(!this.moles[index]){
                this.activateMole(index);
            }
        },
        activateMole: function(id){
            // 実際にmolesに情報を更新する
            this.updateMole(id,true);
            molesTimers[id] = setTimeout(this.deactivateMole.bind(this,id),2500);
        },
        deactivateMole: function(id){
            // molesに対して情報を更新する
            this.updateMole(id,false);
        },
        updateMole: function(id, active) {
            const moles = this.moles.slice(0);
            moles[id] = active;
            this.moles = moles;
        }
    },
    //子要素を親で要素で利用する
    components:{
        Moles: Moles,
        Counter: Counter
    }
}
  
</script>

<style>
.whackamole {
  font-family: Bungee,cursive;
  max-width: 800px;
  width: 100%;
  margin: auto;
  margin-top: 20px;
}
.logo {
  text-align: center;
  margin: 30px;
}
.start-game {
    margin: auto;
    display: block;
}
button {
  font-family: Bungee,cursive;
  padding: 20px;
  border-radius: 3px;
  border: 0;
  background-color: #52b1d6;
  color: #fff;
  font-size: 1em;
  cursor: pointer;
  transition: background-color .2s ease;
}
.counters-container {
  display: flex;
  justify-content: space-around;
  margin-bottom: 20px;
}

</style>
