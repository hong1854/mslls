<template>
  <div id="home">
    <Nav-Bar class="home-navbar"><div slot="center">女人街</div></Nav-Bar>
    <HomeSwiper :banner="banner"></HomeSwiper>
    <Recommend-view :recommends="recommend"></Recommend-view>
    <Feature></Feature>
    <TabControl :title="['流行','新款','精选']"></TabControl>
    <ul>
      <li>1</li>
      <li>2</li>
      <li>3</li>
      <li>4</li>
      <li>5</li>
      <li>6</li>
      <li>7</li>
      <li>8</li>
      <li>9</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>2</li>
      <li>3</li>
      <li>4</li>
      <li>5</li>
      <li>6</li>
      <li>7</li>
      <li>8</li>
      <li>9</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>2</li>
      <li>3</li>
      <li>4</li>
      <li>5</li>
      <li>6</li>
      <li>7</li>
      <li>8</li>
      <li>9</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
    </ul>
    
  </div>
  
</template>

<script>
import NavBar from "components/common/navBar/NavBar";
import HomeSwiper from "./chlidComps/HomeSwiper";
import RecommendView from "./chlidComps/RecommendView";
import Feature from "./chlidComps/Feature.vue"

import TabControl from "components/content/tabControl/TabControl"



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
    RecommendView,
    Feature,
    TabControl,
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
#home{
    padding-top:44px;
  }
.home-navbar {
  background-color: var(--color-tint);
  color: #fff;
  font-size:13px;

  position: fixed;
  left:0;
  right:0;
  top:0;
  z-index:9;
}
</style>