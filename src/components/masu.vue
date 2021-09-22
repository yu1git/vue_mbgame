<template>
  <div>
  <div class="waku alert-info" v-on:click="change" >{{hyouji}}</div>
  </div>
</template>

<script>
export default {
    name:"Masu",
    props:{
      count:Number,
      number:Number,
    },
    data(){
      return{
        hyouji:"",
      }
    },
    methods: {
      change(){
        console.log("key="+this.number);
      
        if(this.count%2===0){
        this.hyouji="〇";
        this.$emit('countadd',this.number,this.hyouji);
        
        }else{
        this.hyouji="×";
        this.$emit('countadd',this.number,this.hyouji);
        
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
  color: rgb(77, 184, 255);
}
</style>