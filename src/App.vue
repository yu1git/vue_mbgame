<template>
  <div>
    <h1 class="bg-info text-white display-4 px-3">〇✕ゲーム</h1>
  <div id="app" class="continer  mx-auto mt-4 board" style="width:450px">
    <Masu  v-for='n of 9' v-bind:key='n' v-bind:count="count" 
    v-bind:number="n" v-on:countadd="countadd"  />
    <p class="message">{{message}}</p>
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
       check:Array(9).fill(0),
      message:'',
     }
  },
  methods: {
    makeArrays(array){
      // 縦の配列
    const columnA = array.filter((n,index) => index % 3 === 0);
    const columnB = array.filter((n,index) => index % 3 === 1)
    const columnC = array.filter((n,index) => index % 3 === 2)

    // 横の配列
    const rowA = array.slice(0,3)
    const rowB = array.slice(3,6)
    const rowC = array.slice(6,9)

    // 斜めの配列
    const diagonalA = [array[0],array[4],array[8]]
    const diagonalB = [array[2],array[4],array[6]]

    // 8個の配列を持った配列として返す
    return [columnA,columnB,columnC,rowA,rowB,rowC,diagonalA,diagonalB]
  
    },
    checkWin(array){
      if(array.every(n=>n === "〇")){
        this.message='〇の勝利';
      }else if(array.every(n=>n==="×")){
        this.message='×の勝利';
      }
    },

    countadd(clickNumber,masu){
      this.count++;
      
      this.check[clickNumber-1]=masu;
      console.log(this.check);

      const checkArrays=this.makeArrays(this.check);
      checkArrays.map((array)=>this.checkWin(array));
    },
    
  },
}
</script>

<style>
.board{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
}
</style>