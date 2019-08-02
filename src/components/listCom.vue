<template>
  <div class="list">
    <asideBar :options="menuData"></asideBar>
    <conCom :options="listData" :default="menuData[0].value"></conCom>
    <footerCom :options="listData"></footerCom>
    <coverCom :options="coverOption"></coverCom>
  </div>
</template>

<script>
import asideBar from "./asideBar";
import conCom from "./conCom";
import footerCom from "./footerCom";
import coverCom from "./coverCom";
import dataJson from "../data/data.json";
import menuData from "../data/menu.json";
export default {
  data() {
    return {
      menuData: menuData.menu,
      listData: dataJson.data,
      coverOption: {
        visible: false, //控制显隐
        data: {}
      }
    };
  },
  components: {
    asideBar,
    conCom,
    footerCom,
    coverCom
  }
};
</script>
<style scoped  lang="">
</style>