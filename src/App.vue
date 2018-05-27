<template>
<div class="whackamole">
    <h1 class="logo">
      Whackamole
    </h1>
    <button
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
    v-on:whacked='handleWhack'/>
  </div>
  
</template>

<script>
import Moles from './components/Moles'
import Counter from './components/Counter'
export default {
    name: 'App',
    data: ()=>{
        return{
            score: 0,
            highScore: 20,
            timer: 10,
            moles: [true,false,false,false]
        }
    },
    methods:{
        startGame: function(){
            this.startTimer();
        },
        handleWhack: function(idx){
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
            }
        },
        stopTimer: function(){
            //setInterval を使用して設定された繰り返し動作をキャンセルします。
            clearInterval(this.timerId)
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

</style>
