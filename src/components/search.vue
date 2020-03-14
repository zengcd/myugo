<template>
  <view class="search" :class='{focused: isFocused}'>
    <!-- 搜索栏标签 -->
    <view class="input-box">
      <input type="text" @focus='goSearch'/>
    </view>
    <!-- 搜索的结果 -->
    <view class="content"></view>
  </view>
</template>

<script>
export default {
  data () {
    return {
      isFocused: false
    }
  },
  methods: {
    goSearch () {
      console.log('hello')
      // 当输入框获取焦点时，在父元素添加一个类名 focused
      this.isFocused = true
    }
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
        &.focused {
    .input-box {
      background-color: #eee;
    }
  }
	}
</style>
