<template>
  <div 
    class='mole'
    v-on:click='whacked'
  >
    <h1>{{ mole }}</h1>
  </div>
</template>

<script>
export default {
    name: 'Mole',
    props: ['mole','idx'],
    methods:{
      whacked: function(){
        //親コンポーネントにイベントを送出する。
        //第二引数で特定の値を親に送ることができる。
        this.$emit('whacked', this.idx)
      }
    }
}
</script>


<style>

</style>
