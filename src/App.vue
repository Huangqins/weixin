<script>
import qcloud from "wafer2-client-sdk";
import config from "./config";

export default {
  async created() {
    let user = wx.getStorageSync("userInfo");
    if (!user) {
      qcloud.setLoginUrl(config.service.loginUrl);
      qcloud.login({
        success: function(userInfo) {
          wx.setStorageSync("userInfo", userInfo);
          console.log("登录成功", userInfo);
        },
        fail: function(err) {
          console.log("登录失败", err);
        }
      });
    }
  }
};
</script>

<style>
/* .container {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  padding: 200rpx 0;
  box-sizing: border-box;
} */
/* this rule will be remove */
* {
  transition: width 2s;
  -moz-transition: width 2s;
  -webkit-transition: width 2s;
  -o-transition: width 2s;
}
.btn {
  color: white;
  background: #EA5A49;
  margin-bottom: 10px;
  padding-left: 15px;
  padding-right: 15px;
  border-radius: 2px;
  font-size: 16px;
  line-height: 40px;
  height: 40px;
  width: 100%;
}
.btn:active {
  background: #FA5A49;
}
</style>
