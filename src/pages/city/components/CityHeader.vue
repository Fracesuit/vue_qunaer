<template>
  <div class="header">
    城市选择
    <router-link to="/">
        <div class="iconfont header-back">&#xe624;</div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>
<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  .header
    position relative
    overflow hidden
    line-height: $headerHeight
    height : $headerHeight
    background: $bgcolor
    text-align center
    color :#ffffff
    font-size: .32rem
    .header-back
      position absolute
      width: .64rem
      top: 0
      left: 0
      float: left
      text-align center
      font-size .4rem
      color  #fff
</style>
