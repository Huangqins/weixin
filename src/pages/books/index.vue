<template>
  <div>图书列表页
      <button open-type="getUserInfo" lang="zh_CN" @click="doLogin">你</button>
  </div>

</template>
<script>
import qcloud from 'wafer2-client-sdk'
import config from '../../config'
export default {
  methods: {
    doLogin() {
      console.log(config.service.loginUrl)
       qcloud.setLoginUrl(config.service.loginUrl);
      qcloud.login({
     success: function(userInfo) {
       console.log('登录成功',userInfo)
     },
     fail: function (err) {
       console.log('登录失败', err)
     }
   })
    }
  }
};
</script>
<style>
</style>

