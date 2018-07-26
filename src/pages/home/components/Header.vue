<template>
  <div class="header">
    <div class="header-left"><span class="iconfont icon-back">&#xe624;</span></div>
    <div class="header-input"><span class="iconfont">&#xe632;</span>输入框</div>
    <div class="header-right">城市<span class="iconfont icon-arrow">&#xe64a;</span></div>
  </div>
</template>

<script>
export default {
  name: 'HomeHeader'
}
</script>
<style lang="stylus" scoped>
  /*1 rem=50px  2倍图*/
  /*@import "~@/assets/styles/varibles.styl"  引入别名*/
  @import "~styles/varibles.styl"
  .header
    display flex
    display -webkit-flex
    line-height: .86rem
    background: $bgcolor
    color :#ffffff
    .header-left
      width: .64rem
      float: left
      text-align center
      .icon-back
          font-size .20rem
    .header-input
      flex: 1
      background: #ffffff
      height .62rem
      line-height .62rem
      margin-top .12rem
      padding-left .2rem
      margin-left .2rem
      border-radius .1rem
      color #ccc
      text-align left
    .header-right
      width: 1.24rem
      float: right
      text-align center
      .icon-arrow
        font-size .20rem
        text-align center
</style>
