<template>
  <div class="moles-container">
    <div class="mole"
      v-for="(mole,idx) in molesState"
      v-bind:key = idx
      >
      {{ mole }}
      </div>
  </div>
    
</template>

<script>
export default {
    name: 'Moles',
    //親から子にデータを渡す
    props: ['molesState']
    
}
</script>

<style>

</style>
