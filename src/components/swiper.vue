<template>
    <div class="swiper">
        <swiper :options="swiperOption">
            <swiper-slide v-for="(item,index) in dataImg" :key="index">
                <img :src="item.src" alt="">
            </swiper-slide>
        </swiper>
        <div class="swiper-pagination page"></div>
    </div>
</template>

<script>
import 'swiper/dist/css/swiper.css'
import { swiper, swiperSlide } from 'vue-awesome-swiper'
export default {
    data(){
        return {
            dataImg:[
                {src:require('../images/1.jpg')},
                {src:require('../images/2.jpg')},
                {src:require('../images/3.jpg')}
            ],
            swiperOption:{
                autoplay:true,
                loop:true,
                pagination:{
                    el:'.swiper-pagination',
                    clickable:true
                }
            }
        }
    },
    components: {
        swiper,
        swiperSlide
    }
}
</script>
<style scoped  lang="">

</style>