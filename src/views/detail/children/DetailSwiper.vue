<template>
  <div class="swiper-list">
    <van-swipe :autoplay="2000">
      <van-swipe-item :key="index" v-for="(item, index) in swiperList">
        <img :src="item" @load="swiperLoad" alt="" />
      </van-swipe-item>
    </van-swipe>
  </div>
</template>

<script>
export default {
  name: "DetailSwiper",
  props: {
    swiperList: {
      type: Array,
      // default默认值需要一个函数return一个默认值
      default() {
        return [];
      }
    }
  },
  data() {
    return {
      isLoad: true
    };
  },
  methods: {
    swiperLoad() {
      if (this.isLoad) {
        this.$emit("swiperLoad");
        this.isLoad = false;
      }
    }
  }
};
</script>

<style scoped>
.swiper-list /deep/ .van-swipe__indicator {
  width: 10px;
  height: 10px;
  background-color: white;
  opacity: 0.8;
}

.swiper-list /deep/ .van-swipe__indicator--active {
  background-color: red;
}

/* 取消vant的相对定位 */
.swiper-list /deep/ .van-swipe {
  position: unset;
}

.swiper-list {
  width: 100%;
  position: relative;
  height: 300px;
  overflow: hidden;
}

.swiper-list img {
  width: 100%;
}
</style>
