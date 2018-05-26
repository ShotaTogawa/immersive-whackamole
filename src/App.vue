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
    <div class="moles-container">
      <div class="mole">{{ moles[0]}}</div>
      <div class="mole">{{ moles[1]}}</div>
      <div class="mole">{{ moles[2]}}</div>
      <div class="mole">{{ moles[3]}}</div>
    </div>
  </div>
  
</template>

<script>
export default {
    data: ()=>{
        return{
            score: 10,
            highScore: 20,
            timer: 10,
            moles: [false,false,false,false]
        }
    },
    methods:{
        startGame: function(){
            console.log('start');
        }
    }
  
}
</script>

<style>

</style>
