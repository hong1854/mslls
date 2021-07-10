<template>
  <Swiper>
    <Swiper-item v-for="item in banner" :key="item.link">
      <a :href="item.link">
        <img :src="item.image" alt />
      </a>
    </Swiper-item>
  </Swiper>
</template>
<script>
import {Swiper,SwiperItem} from "components/common/swiper"
export default {
  props:{
    banner:{
      type:Array,
      defaule(){
        return []
      }
    }
  },
  components:{
    Swiper,
    SwiperItem
  }


};
</script>

<style>
</style>