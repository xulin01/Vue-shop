<template>
  <div id="app">
    <Header></Header>
    <Goods v-for="k in list" :key="k.id" :id="k.id" :state="k.goods_state" :count="k.goods_count" :pic="k.goods_img" :name="k.goods_name" :rmb="k.goods_price"  @stateChange="sta">
    <template #c>
      <Cont :init="k.goods_count" @num="fgk(k,$event)"></Cont>
    </template>
    
    </Goods>
    
    
    <Bottom :init="ant" @fa="ff" :all="all" :num="num"></Bottom>
    
  </div>
</template>

<script>
import Axios from 'axios'
import Header from "@/components/Header.vue";
import Goods from "@/components/Goods.vue";
import Bottom from "@/components/bottom.vue";
import Cont from "@/components/Cont.vue";

export default {
  components:{
    Header,Goods,Bottom,Cont

  },
  data() {
    return {
      list:[],
      
    }
  },
  created(){
    this.ge();
    this.sta();
  
  },

methods:{
  async ge(){
  const {data:res} = await Axios.get('https://www.escook.cn/api/cart')
  if(res.status ==200){
  this.list =res.list
  }
  },
  sta(v){
    this.list.some(item =>{
      if(item.id == v.id){
        item.goods_state = v.val
        return true
      }
    })
   
  },
  ff(v){
  this.list.forEach(ite=>ite.goods_state = v)
  },
 fgk(item,e){
  item.goods_count =e
 }
},
 computed:{
  ant(){
    return this.list.every(itm=>itm.goods_state)
  },
  all(){
    return this.list.filter(item=>item.goods_state).reduce((total,item)=>(total +=item.goods_price * item.goods_count),0)
  },
  num(){
    return this.list.filter(it=>it.goods_state).reduce((t,item)=>( t+=item.goods_count),0)
  }
},

}
</script>

<style lang="less">
*{
  margin: 0;
  padding: 0;
}

</style>
