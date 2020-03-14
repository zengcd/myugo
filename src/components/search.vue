<template>
  	 <!-- 搜索栏 -->
	 <view class="search">
      <!-- 搜索框 -->
      <view class="input-box">
       <input type='text'/>
      </view>
       <!-- 搜索结果 -->
      <view class="content"></view>
    </view>
</template>

<script>
  export default {
      data(){
      }
}
</script>

<style lang="less" scoped>
	.search {
		.input-box {
		    background-color: #EB4450;
		    padding: 20rpx;
		    input {
				background-color: #fff;
				border-radius: 6rpx;
			}
		}
	}
</style>
