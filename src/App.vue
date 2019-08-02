<template>
  <div id="app">
    <headerCom></headerCom>
    <navCom></navCom>
    <swiper></swiper>
    <listCom></listCom>
  </div>
</template>

<script>
import headerCom from './components/headerCom'
import navCom from './components/navCom'
import swiper from './components/swiper'
import listCom from './components/listCom'

export default {
  name: 'App',
  render:h => h(App),
  components:{
    headerCom,
    navCom,
    swiper,
    listCom
  }
}
</script>

<style lang="scss">
@import './iconfont/iconfont.css';
@import './scss/reset.scss';
@import './scss/common.scss';
@import './scss/index.scss';
</style>
