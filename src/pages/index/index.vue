<template>
	<view class='container' :style="{height: pageHeight, overflow: 'hidden'}">
<!-- 搜索栏 -->
<search @window-height="handleWindowHeight" />
<swiper indicator-dots>
  <swiper-item :key='item.goods_id' v-for='item in swiperData'>
    <image :src='item.image_src'/>
  </swiper-item>
</swiper>

<!-- 导航菜单 -->
<view class="navs">
  <navigator :key='index' url='' v-for='(item,index) in navsData'>
    <image :src='item.image_src'/>
  </navigator>
</view>

<!-- 樓層商品 -->
<view class="floors">
  <view class="floor" :key="index" v-for="(item,index) in floorData">
    <!-- 标题 -->
    <view class="title">
      <image :src='item.floor_title.image_src'/>
           </view>
    <!-- 列表 -->
    <view class="items">
      <navigator url='' :key="i" v-for="(img,i) in item.product_list">
        <image :src="img.image_src"></image>
      </navigator>
    </view>
       </view>
     </view>
	</view>
</template>

<script>
import search from '@/components/search.vue'
	export default {
		data() {
			return {
        // title: 'Hello',
        pageHeight: 'auto',
         swiperData:[],
         navsData:[],
         floorData:[]
			}
    },
    components:{
      search
    },
		onLoad() {
      this.querySwiperData()
      this.queryNavsData()
      this.queryFloorData()
		},
		methods: {
      querySwiperData () {
  // 获取轮播图数据
  wx.request({
    url: 'https://api-ugo-dev.itheima.net/api/public/v1/home/swiperdata',
    success: (res) => {
      this.swiperData = res.data.message
    }
  })
},
      queryNavsData(){
        // 获取导航菜单数据
        wx.request({
          url:'https://api-ugo-dev.itheima.net/api/public/v1/home/catitems',
          success:(res)=>{
            this.navsData=res.data.message
          }
        })
      },
      queryFloorData(){
        // 获取楼层数据
        wx.request({
          url:'https://api-ugo-dev.itheima.net/api/public/v1/home/floordata',
          success:(res)=>{
            this.floorData=res.data.message
          }
        })
      },
    handleWindowHeight (data) {
  this.pageHeight = data.height + 'px';
}
		}
	}
</script>

<style lang='less'>

	swiper {
		height: 340rpx;
		image {
			width: 750rpx;
			height: 340rpx;
		}
  }
  .navs {
  height: 190rpx;
  display: flex;
  justify-content: space-between;
  padding: 0 30rpx;
  align-items: center;
  navigator {
    width: 128rpx;
    height: 140rpx;
  }
}
.floor {
  .title {
    width: 750rpx;
    height: 60rpx;
    box-sizing: border-box;
    padding: 20rpx 0 0 10rpx;
    background-color: #f4f4f4;
  }
  .items {
    padding: 20rpx 16rpx;
    overflow: hidden;
    navigator {
      float: left;
      margin-left: 10rpx;
      &:first-child {
        width: 232rpx;
        height: 386rpx;
        margin-left: 0;
      }
      &:nth-child(2),
      &:nth-child(5) {
        width: 273rpx;
        height: 188rpx;
      }
      &:nth-child(3),
      &:nth-child(4) {
        width: 193rpx;
        height: 188rpx;
      }
      &:nth-last-child(-n + 2) {
        margin-top: 10rpx;
      }
    }
  }

  &:first-child {
    .items {
      navigator {
        width: 232rpx;
        height: 188rpx;
        &:first-child {
          width: 232rpx;
          height: 386rpx;
        }
      }
    }
  }
}
</style>
