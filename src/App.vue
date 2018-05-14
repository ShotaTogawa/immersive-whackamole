<template>
  <div class ='whackamole'>
    <div class='logo'>Whack-a-mole!</div>
    <button class='game-start' v-on:click='gameStart'>start round</button>
    <div class='counters-containers'>
      <div class='counter'>
        <h1>whacks:</h1>
        <h2>{{ score }}</h2>
      </div>
      <div class='counter'>
        <h1>high score:</h1>
        <h2>{{ highscore }}</h2>
      </div>
      <div class='counter'>
        <h1>timer:</h1>
        <h2>{{ timer }}</h2>
      </div>

      <div class='moles-container'>
        <div class='mole'>{{ moles[0]}}</div>
        <div class='mole'>{{ moles[1]}}</div>
        <div class='mole'>{{ moles[2]}}</div>
        <div class='mole'>{{ moles[3]}}</div>
      </div>
    </div>
  </div>  
</template>

<script>
export default {
  data: () =>{
    return{
      score: 3,
      highscore: 15,
      timer: 0,
      moles: [ false, false, false, false ]
    };
  },

  methods: {
    gameStart: () =>{
      alert('game start');
    }
  }
}
</script>

<style>

.counter{
    margin: 10px;
    display: inline-block;
  }

  .mole{
    margin: 10px;
    display: inline-block;
  }

</style>
