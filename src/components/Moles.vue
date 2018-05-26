<template>
  <div class="moles-container">
    <Mole class="mole"
      v-for="(mole,idx) in molesState"
      v-bind:mole = mole
      v-bind:key = idx
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
    }
    
}
</script>

<style>

</style>
