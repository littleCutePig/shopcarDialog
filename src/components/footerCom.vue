<template>
    <div class="footer">
        <p>
            <span class="num" v-text="total" @click="showCover"></span>
            <i class="iconfont icon-cart"></i>
        </p>
        <p>结算：￥<span v-text="totalPrice"></span></p>
    </div>
</template>

<script>

export default {
    props:['options'],
    data(){
        return {
            footList:[],
            obj:{}
        }
    },
    watch:{
        footList:{
            handler(n,o){
                console.log(n)
            },
            deep:true
        },
        obj:{
            handler(n,o){
                console.log(n)
            },
            deep:true,
            immediate:true
        }
    },
    created(){
        this.$bus.$on('tooFooterEvent',(val,i,menuSelete) => {
            //数组去重：相同数据只存一次
            //设置一个空对象
            //用key去保存对象的信息
            // debugger
            // if(!this.obj[menuSelete+index]&&this.obj[menuSelete+index]!==0){
            //     //obj没有该键名的时候，就可以push
            //     this.footList.push(val)
            //     this.obj[menuSelete+index]=this.footList.length-1
            //     console.log(this.obj)
            // }else{
            //     //替换相同项
            //     console.log(index)
            //     let index=this.obj[menuSelete+index]
                
            //     console.log(this.obj)
            //     this.footList.splice(index,1,val)
            // }
            if(!this.obj[menuSelete+i]&&this.obj[menuSelete+i]!==0){
                this.footList.push(val)
                this.obj[menuSelete+i]=this.footList.length-1
            }else{
                let index = this.obj[menuSelete+i]
                this.footList.splice(index,1,val)
            }
        })
    },
    computed:{
        total(){//个数
        return this.footList.reduce((total,current)=>{
            return total+current.count
        },0)
        },
        totalPrice(){//总价
        return this.footList.reduce((total,current)=>{
            return total+current.count*current.price
        },0)
        }
  },
  methods:{
    /**
    * 遮罩层弹出
    */
    showCover(){
      this.$bus.$emit('showCoverEvent',this.footList)
    }
  }
}
</script>
<style scoped  lang="">

</style>