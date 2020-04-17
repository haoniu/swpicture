<template>
  <view class="content">
    <!-- <image class="logo" src="/static/logo.png"></image> -->
    <uni-segmented-control :current="current" :values="items" @clickItem="onClickItem"
      style-type="text" active-color="#333"></uni-segmented-control>
    <view class="content">
      <view v-if="current === 0">
        <home-recommend></home-recommend>
      </view>
      <view v-if="current === 1">
        <home-category></home-category>
      </view>
      <view v-if="current === 2">
        <home-new></home-new>
      </view>
      <view v-if="current === 3">
        <home-album></home-album>
      </view>
    </view>

  </view>
</template>

<script>
import { uniBadge, uniSegmentedControl } from "@dcloudio/uni-ui";
import homeAlbum from "./home-album";
import homeCategory from "./home-category";
import homeNew from "./home-new";
import homeRecommend from "./home-recommend";

export default {
  components: {
    uniBadge,
    homeNew,
    homeAlbum,
    homeCategory,
    homeRecommend,
    uniSegmentedControl
  },
  data() {
    return {
      items: ["推荐", "分类", "最新", "专辑"],
      current: 0
    };
  },
  onLoad() {
    // uni.request({
    //   url:
    //     "http://web.juhe.cn:8080/finance/stock/hs?key=ed1e095104f59f0915b61f6642ff523a",
    //   data: {
    //     gid: "sh601009"
    //   },
    //   success: res => {
    //     console.log(res);
    //   }
    // });
  },
  methods: {
    onClickItem(e) {
      if (this.current !== e.currentIndex) {
        this.current = e.currentIndex;
      }
    }
  }
};
</script>

<style>
.content {
  text-align: center;
  height: 400upx;
}

.logo {
  height: 200upx;
  width: 200upx;
  margin-top: 200upx;
}

.title {
  font-size: 36upx;
  color: #8f8f94;
}
</style>
