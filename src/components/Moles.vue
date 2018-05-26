<template>
  <div class="moles-container">
    <Mole class="mole"
      v-for="(mole,idx) in molesState"
      v-bind:mole='mole'
      v-bind:key='idx'
      v-bind:idx='idx'
      v-on:whacked='handleWhacked'
      />
  </div>
    
</template>

<script>
import Mole from './Mole'
export default {
    name: 'Moles',
    //親から子にデータを渡す
    props: ['molesState'],
    components:{
      Mole: Mole
    },
    methods:{
      handleWhacked: function(idx){
        this.$emit('whacked', idx)
      }
    }
    
}
</script>

<style>

</style>
