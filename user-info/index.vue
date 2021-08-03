<!--
 * @Author: linj
 * @Email: 993353454@qq.com
 * @Date: 2020-09-08 18:14:25
 * @Description:微信小程序获取用户信息组件
 name:按钮显示文字
 click: 返回用户信息
 eg:
 <lj-user-info @click="getUserInfo">
</lj-user-info>
-->
<template>
  <!-- <view class=""> -->
  <button class="btn-none"
    @click="checkUserInfo"
    @getuserinfo="checkUserInfo">
    <slot>
      {{ name||'确定' }}
    </slot>
  </button>
  <!-- #ifdef MP-WEIXIN -->
  <!-- #endif -->
  <!-- </view> -->
</template>

<script>
import { mapActions, mapMutations } from 'vuex'
import { login, P } from 'lj-utils/microApi'
export default {
  props: {
    name: {
      type: String,
      default: '',
    }
  },
  components: {

  },
  onLoad(argData) {

  },
  onShow() {

  },
  onReady() {

  },
  onUnload() {

  },
  computed: {

  },
  data() {
    return {

    }
  },
  methods: {
    ...mapActions(['UpdateUser']),
    async checkUserInfo() {
      let userInfo
      // #ifdef MP-WEIXIN
      userInfo = await P('getUserProfile', { desc: '数据展示' }).catch(err => {
        console.error('checkUserInfo', err)
      })
      // #endif
      // #ifdef MP-ALIPAY
      userInfo = await P('getUserInfo', { provider: 'alipay' }).catch(err => {
        console.error('checkUserInfo', err)
      })
      // #endif
      console.info('userInfo:', userInfo)
      if (userInfo && userInfo.iv) {
        let res = await this.UpdateUser(userInfo.userInfo)
        console.error('setUserInfo', res)
        this.$emit('click', true)
      } else {
        console.error('请先同意授权!')
        this.$emit('click', false)
      }
      login(1)
    },
  },
}
</script>

<style lang="scss">
</style>
