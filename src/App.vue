<template>
  <div>
    <h1 class="bg-info text-white display-4 px-3">〇✕ゲーム</h1>
  <div id="app" class="continer  mx-auto mt-4 board" style="width:450px">
    <Masu  v-for='n of 9' v-bind:key='n' v-bind:count="count" v-on:countadd="countadd" />

  </div>
  </div>
</template>

<script>
import Masu from "./components/masu.vue";

export default {
  name: 'App',
  components: {
    Masu
  },
  data(){
     return{
       //手番用のカウント
       count:0
       //勝敗判定用の配列
      
     }
  },
  methods: {
    countadd(){
      this.count++
    }
  },
}
</script>

<style>
.board{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
}
</style>