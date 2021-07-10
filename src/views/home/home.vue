<template>
  <div id="home">
    <Nav-Bar class="home-navbar"><div slot="center">女人街</div></Nav-Bar>
    <HomeSwiper :banner="banner"></HomeSwiper>
    <recommend-view :recommends="recommend"></recommend-view>
  </div>
</template>

<script>
import NavBar from "components/common/navBar/NavBar";
import HomeSwiper from "./chlidComps/HomeSwiper";
import RecommendView from "./chlidComps/RecommendView";



import {getHomedata} from "network/home"

export default {
  name: "home",
  data(){
    return {
      banner:[],
      recommend:[],
    }
  },
  components: {
    NavBar,
    HomeSwiper,
    RecommendView
  },
  created() {
    getHomedata().then(res=>{
      this.result = res
      this.banner = res.data.banner.list
      this.recommend = res.data.recommend.list
    })
  },
};
</script>

<style >
.home-navbar {
  background-color: var(--color-tint);
  color: #fff;
  font-size:13px;
}
</style>