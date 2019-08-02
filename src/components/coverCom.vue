<template>
    <div class="cover" v-if="options.visible">
        <div class="cover-con">
            <div class="list-item" v-for="(item,index) in options.data" :key="index">
                <span>{{item.title}}</span><span>{{item.price}}</span>
                <p><span @click="item.count === 0?0 : item.count--">-</span> <span>{{item.count}}</span><span @click="item.count++">+</span></p>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    props:['options'],
    data(){
        return {

        }
    },
    created(){
        console.log("createdCover")
        let vm=this
        vm.$bus.$on('showCoverEvent',val => {
            vm.options.visible=!vm.options.visible
            vm.options.data=val
            console.log(val)
        })
    }
}
</script>
<style scoped  lang="">

</style>