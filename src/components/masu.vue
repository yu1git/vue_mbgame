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
      //check:{Number:String}
      //?
      //check:String
    },
    data(){
      return{
        hyouji:"",
      }
    },
    methods: {
      change(){
        console.log("key="+this.number)
      
        if(this.count%2===0){
        this.hyouji="〇";
        // this.count++; countは親で管理する
        this.$emit('countadd',this.count)
        //this.$set(this.check,this.number,"〇")
        //this.$emit('checkar',this.number,"〇")
        }else{
          this.hyouji="×";
          // this.count++
        this.$emit('countadd',this.count)
        //this.$set(this.check,this.number,"×")

        //this.$emit('checkar',this.number,"×")

        }
        //console.log(this.check);
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