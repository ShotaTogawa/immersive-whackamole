<template>
<div class="whackamole">
    <h1 class="logo">
      Whackamole
    </h1>
    <button
    v-on:click='startGame'>
      Start Game
    </button>
    <div class="counters-container">
      <div class="counter">
        <h1>Score:</h1>
        <h2>{{ score }}</h2>
      </div>
      <div class="counter">
        <h1>High Score:</h1>
        <h2>{{ highScore }}</h2>
      </div>
      <div class="counter">
        <h1>Timer:</h1>
        <h2>{{ timer }}</h2>
      </div>
    </div>
    <!--this.$emitで子から送られきたイベントでv-onでリッスンできる-->
    <Moles 
    v-bind:molesState='moles'
    v-on:whacked='handleWhack'/>
  </div>
  
</template>

<script>
import Moles from './components/Moles'
export default {
    name: 'App',
    data: ()=>{
        return{
            score: 10,
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
            console.log('whacked ' + idx)
        }
    },
    //子要素を親で要素で利用する
    components:{
        Moles: Moles
    }
}
  
</script>

<style>

</style>
