<template>
    <div class="aside">
        <span v-for="(el,ind) in options" :key="ind" v-text="el.name" :class="{active:i === ind}" @click="asideBtn(ind,el.value)"></span>
    </div>
</template>

<script>

export default {
    props:['options'],
    data(){
        return {
            i:0
        }
    },
    methods:{
        asideBtn(ind,val){
            // console.log(val)
            this.$bus.$emit('menuEvent',val)
            this.i = ind;
        }
    }
}
</script>
<style scoped  lang="">

</style>