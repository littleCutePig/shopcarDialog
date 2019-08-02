<template>
    <div class="nav">
        <span v-for="(item,index) in navData" v-text="item" :key="index" :class="{active:i === index}" @click="tab(index)"></span>
    </div>
</template>

<script>

export default {
    data(){
        return {
            i:0,
            navData:['点菜','评价','商家']
        }
    },
    methods:{
        tab(val){
            this.i = val
        }
    }
}
</script>
<style scoped  lang="">

</style>