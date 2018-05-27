<template>
  <div v-bind:class='classObject'>
    <Mole class="mole"
      v-for="(mole,idx) in molesState"
      v-bind:active='mole'
      v-bind:key='idx'
      v-bind:moleId='idx'
      v-on:whacked='handleWhacked'
      />
  </div>
    
</template>

<script>
import Mole from './Mole'
export default {
    name: 'Moles',
    //親から子にデータを渡す
    props: ['molesState','gameActive'],
    components:{
      Mole: Mole
    },
    methods:{
      handleWhacked: function(moleId){
        this.$emit('whacked', moleId)
      }
    },
    computed:{
      classObject: function(){
        return{
          'moles-container': true,
          'game-active': !!this.gameActive
        }
      }
    }
    
}
</script>

<style>
.moles-container {
  display: flex;
  justify-content: space-between;
  opacity: 0.5;
  transition: opacity 0.3s ease;
}

.moles-container.game-active {
  opacity: 1;
}

</style>
