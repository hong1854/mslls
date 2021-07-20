<template>
  <div id="home">
    <Nav-Bar class="home-navbar"><div slot="center">女人街</div></Nav-Bar>
    <HomeSwiper :banner="banner"></HomeSwiper>
    <Recommend-view :recommends="recommend"></Recommend-view>
    <Feature></Feature>
    <TabControl
      :title="['流行', '新款', '精选']"
      class="tob-control"
      @tabclick="tabclick"
    ></TabControl>
    <GoodsLite :goods="showgoods"></GoodsLite>
  </div>
</template>

<script>
import NavBar from "components/common/navBar/NavBar";
import HomeSwiper from "./chlidComps/HomeSwiper";
import RecommendView from "./chlidComps/RecommendView.vue";
import Feature from "./chlidComps/Feature.vue";
import GoodsLite from "components/content/goods/GoodsList";

import TabControl from "components/content/tabControl/TabControl";

import { getHomedata, getHomeGoods } from "network/home";

export default {
  name: "home",
  data() {
    return {
      banner: [],
      recommend: [],
      goods: {
        pop: { page: 0, list: [] },
        new: { page: 0, list: [] },
        sell: { page: 0, list: [] },
      },
      currentType:'pop'
    };
  },
  computed:{
      showgoods(){
        return this.goods[this.currentType].list
      }
    },
  components: {
    NavBar,
    HomeSwiper,
    RecommendView,
    Feature,
    TabControl,
    GoodsLite,
  },
  methods: {
    /**
     * 网络请求方法
     */

    getHomedata() {
      getHomedata().then((res) => {
        this.result = res;
        this.banner = res.data.banner.list;
        this.recommend = res.data.recommend.list;
      });
    },
    getHomeGoods(type) {
      const page = this.goods[type].page + 1;
      getHomeGoods(type, page).then((res) => {
        console.log(res);
        this.goods[type].list.push(...res.data.list);
        this.goods[type].page += 1;
      });
    },
    /**
     * 时间方法
     */
    tabclick(index) {
      switch(index){
        case 0 :
          this.currentType = 'pop'
          break
        case 1 :  
          this.currentType = 'new'
          break
        case 2 :
          this.currentType = "sell"  
          break
       }
    },
  },
  created() {
    this.getHomedata();
    this.getHomeGoods("pop");
    this.getHomeGoods("new");
    this.getHomeGoods("sell");
  },
};
</script>

<style >
#home {
  padding-top: 44px;
}
.home-navbar {
  background-color: var(--color-tint);
  color: #fff;
  font-size: 13px;

  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 9;
}
.tob-control {
  position: sticky;
  top: 44px;
  z-index: 9;
}
</style>