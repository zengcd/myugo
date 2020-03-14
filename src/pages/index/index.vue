<template>
	<view class="container">
		<!-- 搜索栏 -->
		<view class="search">
  <!-- 搜索框 -->
  <view class="input-box">
    <input type='text'/>
  </view>
  <!-- 搜索结果 -->
  <view class="content"></view>
</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
.search .input-box {
  background-color: #EB4450;
  padding: 20rpx;
}
.search .input-box input {
  background-color: #fff;
}
</style>
