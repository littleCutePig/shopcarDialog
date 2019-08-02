<template>
  <div class="content">
    <div v-for="(el,ind) in shopList" :key="ind">
        <img :src="el.fontImg" alt="">
        <div class="text">
            <h3 v-text="el.title"></h3>
            <p class="desc">
                <span v-for="(item,index) in el.description" v-text="item" :key="index"></span>
            </p>
            <p class="good">
                <span>月售{{el.good.sale}}</span>
                <span>赞{{el.good.zan}}</span>
            </p>
            <div class="box">
                <p><span>￥</span><span v-text="el.price"></span></p>
                <p>
                    <span v-if="el.count" @click="el.count--">-</span>
                    <span v-if="el.count" v-text="el.count"></span>
                    <span @click="addFun(el,ind)">+</span>
                </p>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["options","default"],
  data() {
    return {
      shopList: [],
      menuSelete:null
    };
  },
  methods:{
      addFun(el,ind){
          el.count++
          console.log(el,ind)
          this.$bus.$emit('tooFooterEvent',el,ind,this.menuSelete)
      }
  },
  created() {
    this.shopList = this.options[this.default].list;
    this.menuSelete = this.default
    this.$bus.$on("menuEvent", val => {
        this.menuSelete = val;
        this.shopList = this.options[val].list
    });
  }
};
</script>
<style scoped  lang="">
</style>