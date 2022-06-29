<template>
  <div class="bottom">
    <input type="checkbox" id="q" @change="som" :checked="init"> <label for="q">全选</label> <span>合计:<strong>${{all}}</strong></span> <button>结算(  {{num}}  )</button>
  </div>
</template>

<script>
export default {
  props:{
    init:{
      type:Boolean
    },
    all:{
      type:Number,
      default:0
    },
      num:{
      type:Number,
      default:0
    }
  },
  methods:{
    som(e){
      this.$emit('fa',e.target.checked)
    }
  }
}
</script>

<style lang="less">
.bottom{
    width: 100%;
    height: 50px;
    background-color: #fff;
    border: 1px solid #ccc;
    position: fixed;
    bottom: 0;
    display: flex;
    align-items: center;
     input{
            margin-left:10px ;
        }
    label{
        margin-left: 5px;
        margin-right: 60px;
    }
    span strong{
        font-size: 20px;
        font-weight: 550;
        color: red;
        margin-left: 5px;
    }
    button{
       width: 100px;
       height: 40px;
       background-color: blue;
       color: #fff;
       border: 0;
       border-radius: 30px;
      position: absolute;
      right: 8px;
      bottom: 4px;
    }
}
</style>