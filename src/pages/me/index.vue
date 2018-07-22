<template>
  <div class="container">
    <div class="userinfo">
      <img :src="userinfo.avatarUrl" alt="">
      <p>{{userinfo.nickName}}</p>
    </div>
    <YearProgress></YearProgress>
    <button class="btn" @click="scanBook">添加图书</button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      userinfo: {}
    }
  },
  methods: {
    scanBook() {
      wx.scanCode({
        success: function(res) {
          console.log(res)
        }
      })
    }
  },
  created() {
    this.userinfo = wx.getStorageSync('userInfo');
    console.log(this.userinfo)
  },
}
</script>
<style lang="scss">
.container {
  padding: 0 30rpx;
  .userinfo {
    margin-top:100rpx;
    text-align: center;
    img {
      width: 150rpx;
      height: 150rpx;
      margin: 20rpx;
      border-radius: 50%;
    }
  }
}
</style>



