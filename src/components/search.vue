<template>
  <view class="search" :class="{focused: isFocused}">
    <!-- 搜索栏标签 -->
    <view class="input-box">
      <input :placeholder="placeholder" type="text" @focus="goSearch" />
      <text class="cancel" @click="handleCancel">取消</text>
    </view>
    <!-- 搜索的结果 -->
    <view class="content"></view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      isFocused: false,
      placeholder: ""
    };
  },
  methods: {
    goSearch() {
      console.log("hello");
      // 当输入框获取焦点时，在父元素添加一个类名 focused
      this.isFocused = true;
      this.placeholder = "请输入想要的商品";
      // 触发父组件自定义事件
      this.$emit("window-height", {
        height: uni.getSystemInfoSync().windowHeight
      });
    },
    handleCancel() {
      // 取消动作：恢复原始状态
      this.isFocused = false;
      this.placeholder = "";
      // 取消时操作
      this.$emit("window-height", {
        pageHeight: "auto"
      });
    }
  }
};
</script>

<style lang="less" scoped>
.search {
  .content {
    position: absolute;
    top: 90rpx;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 9;
    background-color: #fff;
    display: none;
  }
  .input-box {
    background-color: #eb4450;
    position: relative;
    padding: 20rpx 16rpx;
    display: flex;
    input {
      background-color: #fff;
      padding-left: 55rpx;
      flex: 1;
    }
    .cancel {
      display: none;
    }
    &::before {
      content: "";
      display: none;
      width: 32rpx;
      height: 32rpx;
      position: absolute;
      top: 50%;
      transform: translate(15rpx, -50%);
      background-image: url("http://static.botue.com/ugo/images/icon_search%402x.png");
      background-size: 32rpx;
    }
    &::after {
      content: "搜索";
      position: absolute;
      left: 50%;
      top: 50%;
      padding-left: 40rpx;
      transform: translate(-50%, -50%);
      font-size: 24rpx;
      color: #ccc;
      background-image: url("http://static.botue.com/ugo/images/icon_search%402x.png");
      background-size: 32rpx;
      background-repeat: no-repeat;
    }
  }
  &.focused {
    .content {
      display: block;
    }
    .input-box {
      background-color: #eee;
      &::after {
        display: none;
      }
      &::before {
        display: block;
      }
    }
    .cancel {
      display: block;
      width: 100rpx;
      height: 50rpx;
      line-height: 50rpx;
      text-align: center;
      font-size: 30rpx;
      display: block;
    }
  }
}
</style>
