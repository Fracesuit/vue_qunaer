<template>
  <div>
    <router-link tag="div" to="/" class="header-abs" v-if="showAbs">
      <div class="iconfont icon-abs-back">&#xe624;</div>
    </router-link>
    <div class="header-fixed" v-else :style="opacityStyle">
      景点详情
      <router-link to="/">
        <div class="iconfont icon-fixed-back">&#xe624;</div>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handlerWindowScroll () {
      let scrollTop = document.documentElement.scrollTop + document.body.scrollTop
      this.showAbs = scrollTop < 60
      if (scrollTop < 140 && !this.showAbs) {
        let opacity = scrollTop / 140
        this.opacityStyle.opacity = opacity
      }
    }
  },
  mounted () {
    window.addEventListener('scroll', this.handlerWindowScroll)
  },
  destroyed () {
    window.removeEventListener('scroll', this.handlerWindowScroll)
  }
}
</script>
<style scoped lang="stylus">
  @import "~styles/varibles.styl"
  .header-abs
    position absolute
    left .2rem
    top .2rem
    width: .8rem
    height .8rem
    border-radius .4rem
    line-height .8rem
    text-align: center
    background: rgba(0, 0, 0, .8)
    .icon-abs-back
      color #fff
      font-size .4rem

  .header-fixed
    z-index 1
    position fixed
    left: 0
    top: 0
    right 0
    overflow hidden
    line-height: $headerHeight
    height: $headerHeight
    background: $bgcolor
    text-align center
    color: #ffffff
    font-size: .32rem
    .icon-fixed-back
      position absolute
      width: .64rem
      top: 0
      left: 0
      float: left
      text-align center
      font-size .4rem
      color #fff
</style>
