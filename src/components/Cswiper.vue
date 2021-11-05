<template>
   <Swiper
    v-if="list.length>0"
    :autoPlay='autoPlay'
    :showIndicator='showIndicator'
    :interval="interval"
    :duration="duration"
    >
       <Slide v-for="(item,index) in list" :key="index"  @click="clickSwiper(item)">
         <img :src=" item.img_url"/>
       </Slide>
  </Swiper>
</template>
 
<script>
import { Swiper, Slide } from 'vue-swiper-component';
export default {
    name:'cswiper',
  props: {
    /**
     * 轮播图数据
     */
    list:Array,
    /**
     * 是否自动轮播
     */
    autoPlay:{
      type:Boolean,
      default:true
    },
    /**
     * 是否显示轮播的点
     */
    showIndicator:{
      type:Boolean,
      default:false
    },
     /**
     * 每两次隔多久滚动一次
     */
    interval:{
      type:Number,
      default:2500
    },
     /**
     * 每次滚动一页需要多久
     */
    duration:{
      type:Number,
      default:500
    },
  },
  data () {
    return {
 
    };
  },
 
  components: {
    Swiper,
    Slide
  },
 
  computed: {},
  mounted() {},
  watch: {}
}
 
</script>
<style lang='scss' scoped>
 
</style>