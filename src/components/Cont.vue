<template>
<div class="cont">
  <button @click="z">-</button> <input type="text" disabled :value="init"> <button @click="j">+</button>
   
  </div>
 
</template>

<script>
export default {

 props:{
  init:{
    type:Number,
    default:1
  }
 },
 methods:{
  j(){
    this.$emit('num',this.init +1)
  },
  z(){
    if(this.init - 1 >=1){
    this.$emit('num',this.init -1)
    }
  },
 }
}
</script>

<style lang="less">
.cont{

  height: 20px;
    position: absolute;
    bottom: 10px;
    right: 10px;
    button{
    width: 20px;
    height: 20px;
    border: 0;
}
input{
    width: 30px;
    height: 20px;
    text-align: center;

   
}
}


</style>