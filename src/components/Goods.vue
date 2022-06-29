<template>
  <div class="goods">
   
    <input type="checkbox" @change="changeState" class="inp" :checked="state"> <img :src="pic"> <span>{{name}} <strong>${{rmb}}</strong></span> 
    <slot name="c"></slot>
  </div>
</template>

<script>
import Cont from '@/components/Cont.vue'
export default {
    props:{
        id:{
            type:Number
        },
        state:{
            type:Boolean,
        },
        pic:{
            type:String
        },
        name:{
            type:String,
            default:''
        },
        rmb:{
            type:Number,
            default:0
        },
        count:{
            type:Number
        }
    },
    components:{
        Cont,
    },
    methods:{
        changeState(e){
            const c=e.target.checked;
            this.$emit('stateChange',{id:this.id,val:c})
        }
    }
}
</script>

<style lang="less">
    .goods{
        width: 100%;
        height: 150px;
        display: flex;
        align-items: center;
        margin-top: 20px;
        margin-bottom: 35px;
        border-bottom: 1px solid #ccc;
       position:relative;
        .inp{
            margin-left:10px ;
        }

        img{
            width: 100px;
            height: 100px;
            margin-left: 10px;
        }
        span{
            height: 120px;
            position: relative;
            margin-left: 30px;
        }
        strong{
            position: absolute;
            bottom: 0;
            left: 0;
        }
        .goods:nth-child(2){
        background-color: red;
        color: red;
       }
    }

</style>