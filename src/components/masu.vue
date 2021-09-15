<template>
  
  <div class="waku" v-on:click="change" >{{hyouji}}</div>
</template>

<script>
export default {
    name:"Masu",
    props:{
      count:Number
    },
    data(){
      return{
        hyouji:"",
      }
    },
    methods: {
      change(){
        if(this.count%2===0){
        this.hyouji="〇";
        // this.count++; countは親で管理する
        this.$emit('countadd',this.count)
        console.log(this.count);
        }else{
          this.hyouji="×";
          // this.count++
        this.$emit('countadd',this.count)

          console.log(this.count);

        }
      }
    }
}
</script>

<style>
.waku {
  height: 150px;
  width: 150px;
  border: 1px solid black;
  line-height: 150px;
  font-size: 90px;
  text-align: center;
}
</style>