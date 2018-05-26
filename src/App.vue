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
            console.log('start');
        },
        handleWhack: function(idx){
            this.score++;
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
