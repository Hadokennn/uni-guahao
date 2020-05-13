<template>
  <div class="page-my">
    <div class="page-my--list">
      <div class="page-my--item" v-for="(item, index) in list" :key="index" @click="go(index)">
        <span :class="'page-my--icon page-my--icon-' + item.icon"></span>
        <span class="page-my--item-center">{{item.text}}</span>
        <span class="page-my--icon page-my--icon-right"></span>
      </div>
    </div>
    <div class="page-my--tip">
      如果您的问题没有被解决，请关注【微医健康】公众号，享受更多的服务和帮助
    </div>
    <g-auth ref="auth"></g-auth>
    <fm-agent></fm-agent>
  </div>
</template>

<script>
export default {
  data () {
    return {
      list: [
        {icon: 'order', text: '我的挂号', link: '/pages/my-order/main'},
        {icon: 'consult', text: '我的问诊', link: '/pages/consult-order/main'},
        {icon: 'patient', text: '家庭联系人', link: '/pages/patient/list/main'}
      ],
    }
  },
  mounted () {
    // this.$refs.auth.run()
  },
  methods: {
    go (index) {
      // this.$refs.auth.run(true).then(() => {
		// 正常账号
		console.log(this.list[index].link)
		wx.navigateTo({
		  url: this.list[index].link
		})
      // })
    }
  }
}
</script>

<style lang="less">
@import "@/styles/variable.less";
@import "@/styles/function.less";
.page-my {
  height: 100%;
  padding-top: 6px;
  box-sizing: border-box;
  color: #666;
  &--list {
    .borders-h;
    padding-left: 12px;
    background-color: @color-main-white;
  }
  &--item {
    display: flex;
    align-items: center;
    padding-right: 12px;
    height: 50px;
    font-size: 16px;
    position: relative;
    &:not(:nth-last-child(1)) {
      .border(B);
    }
  }
  &--item-center {
    flex: 1;
  }
  &--icon{
    width: 12px;
    height: 12px;
    margin-right: 6px;
    background-repeat: no-repeat;
    background-size: 100% 100%;
  }
  &--icon-order {
    background-image: url("https://kano.guahao.cn/MDU71907452");
  }
  &--icon-consult {
    background-image: url("https://kano.guahao.cn/Hph71907454");
  }
  &--icon-patient {
    background-image: url("https://kano.guahao.cn/WiV71907451");
  }
  &--icon-contact {
    background-image: url("https://kano.guahao.cn/TJw71907453");
  }
  &--icon-right {
    box-sizing: border-box;
    width: 8px;
    height: 8px;
    border-right: 2px solid #c7c7cc;
    border-bottom: 2px solid #c7c7cc;
    transform: rotate(-45deg);
    margin-left: 6px;
  }
  &--contact-btn {
    .btn-reset;
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: transparent;
  }
  &--tip {
    padding: 12px;
    color: #999;
  }
}
</style>
