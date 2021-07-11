<template>
  <div class="tab-control">
    <div v-for="(item, index) in title" :key="item" class="tab-control-item" :class="{active:index ===currentIndex}" @click="itemclick(index)">
      <span>{{ item }}</span>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      currentIndex:0
    }
  },
  methods: {
    itemclick(index){
      this.currentIndex =index
    }
  },
  props: {
    title: {
      type: Array,
      default() {
        return [];
      },
    },
  },
};
</script>
<style scoped>
.tab-control {
  display: flex;
  text-align: center;
  font-size: 15px;
  height: 40px;
  line-height: 40px;

  position: sticky;
  top:44px;
  background-color: #fff;
}
.tab-control-item {
  flex: 1;
}
.tab-control-item span {
  padding: 5px;
}
.active{
  color: var(--color-high-text);
  
}
.active span{
  border-bottom: 3px solid var(--color-high-text);
}
</style>