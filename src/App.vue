<template>
  <div>
    <h1 class="bg-info text-white display-4 px-3">〇✕ゲーム</h1>
  <div id="app" class="continer  mx-auto mt-4 board" style="width:450px">
    <Masu  v-for='n of 9' v-bind:key='n' v-bind:count="count" 
    v-bind:number="n" v-on:countadd="countadd" v-on:checkar="checkar" />

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
      count:0,
       //勝敗判定用の配列
      //check:[0,0,0,0,0,0,0,0,0],
      check:{}
     }
  },
  methods: {
    countadd(){
      this.count++
    },
    checkar(mb){
      // for(let i=0;i<9;i++){
      // if(this.check[i]===0){
      //   this.check[i]=mb;
      // }
      // }
      //this.check[i].push(mb);配列の後ろに追加してしまう
      //オブジェクトを使う？nを使えない
      //this.$set(this.check,'n',mb);
      
      console.log(this.check);
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