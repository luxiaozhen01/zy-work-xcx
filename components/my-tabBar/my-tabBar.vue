<template>
  <view class="tabbar-container">
    <block>
      <view class="tabbar-item" v-for="(item, index) in tabbarList" :class="[item.centerItem ? 'center-item' : '']"  @click='changeItem(item)' :key="index">
        <view class="item-top">
          <image :src="currentItem == item.id ? item.selectedIconPath : item.iconPath"></image>
        </view>
        <view class="item-bottom" :class="[currentItem == item.id ? 'item-active' : '']">
          <text>{{ item.text }}</text>
        </view>
      </view>
    </block>
  </view>
</template>

<script>
export default {
  props: {
    currentPage: {
      type: Number,
      default: 0
    }
  },
  data () {
    return {
      currentItem: 0,
      tabbarList: [
		  {
			id: 0,
		  	pagePath: "/pages/tabbar/work/work",
		  	iconPath: "/static/tabbar/work.png",
		  	selectedIconPath: "/static/tabbar/work-fill.png",
		  	text: "工作",
			centerItem: false
		  }, {
			id: 1,
		  	pagePath: "/pages/tabbar/helper/helper",
		  	iconPath: "/static/tabbar/helper.png",
		  	selectedIconPath: "/static/tabbar/helper-fill.png",
		  	text: "助手",
			centerItem: false
		  } ,{
			id: 2,
		  	pagePath: "/pages/tabbar/usual/usual",
		  	iconPath: "/static/tabbar/usual-fill.png",
		  	selectedIconPath: "/static/tabbar/usual-fill.png",
		  	text: "常用",
			centerItem: true
		  } ,{
			id: 3,
		  	pagePath: "/pages/tabbar/analyse/analyse",
		  	iconPath: "/static/tabbar/analyse.png",
		  	selectedIconPath: "/static/tabbar/analyse-fill.png",
		  	text: "分析",
			centerItem: false
		  } 
		  ,{
			id: 4,
		  	pagePath: "/pages/tabbar/user/user",
		  	iconPath: "/static/tabbar/user.png",
		  	selectedIconPath: "/static/tabbar/user-fill.png",
		  	text: "我的",
			centerItem: false
		  }
      ]
    }
  },
  methods: {
    changeItem (item) {
		this.currentItem = item.id
	  this.$emit('clickTabBar',item.id)
    }
  }
};
</script>
<style lang="scss" scope>
view {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.tabbar-container {
  position: fixed;
  bottom: 0rpx;
  left: 0rpx;
  width: 100%;
  height: 130rpx;
  box-shadow: 0 0 2px #999;
  display: flex;
  align-items: center;
  padding: 5rpx 0;
  color: #999999;
  background-color: #fff;

  /* 针对tabbar的统一处理 */
  .tabbar-item {
    width: 33.33%;
    height: 100rpx;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    .item-top {
      width: 80rpx;
      height: 80rpx;
      // padding: 10rpx;
      image {
        width: 100%;
        height: 100%;
      }
    }
    // 未被选中的导航栏字体
    .item-bottom {
      font-size: 20rpx;
      width: 100%;
    }
    // 被选中的导航栏字体
    .item-active {
      color: #88bf01;
    }
  }

  // 最中间的tabbar导航栏
  .center-item {
    display: block;
    position: relative;
    .item-top {
      flex-shrink: 0;
      width: 110rpx;
      height: 110rpx;
      position: absolute;
      top: -50rpx;
      left: calc(50% - 55rpx);
      border-radius: 100% 100% 0 0;
      // box-shadow: 0 -40px 150px #999;
	  border-top: 1px solid #999;
      background-color: #fff;
    }
    .item-bottom {
      position: absolute;
      bottom: 5rpx;
    }
    .item-active {
      position: absolute;
      bottom: 5rpx;
      color: #88bf01;
    }
  }
}
</style>
