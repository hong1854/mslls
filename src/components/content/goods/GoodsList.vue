<template>
  <div class="goodslist">
    <GoodsListItem
      v-for="item in goods"
      :goodsItem="item"
      :key="item.img"
    ></GoodsListItem>
  </div>
</template>
<script>
import GoodsListItem from "./GoodsListItem.vue";
export default {
  props: {
    goods: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  components: {
    GoodsListItem,
  },
};
</script>
<style>
.goodslist {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

</style>