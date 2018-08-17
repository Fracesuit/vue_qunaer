<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img :src="banner.bannerImg"
           class="banner-img"/>
      <div class="banner-info">
        <div class="banner-title">{{banner.sightName}}</div>
        <div class="banner-number"><span class="iconfont banner-icon">&#xe64a;</span>16</div>
      </div>
    </div>
    <fade-animation>
      <gallary :imgs="banner.gallaryImgs" v-show="imgsShow" @handleGallaryClick="handleGallaryClose"/>
    </fade-animation>
  </div>
</template>

<script>
import Gallary from 'common/gallary/Gallary'
import FadeAnimation from 'common/fade/Fade'

export default {
  name: 'Banner',
  props: {
    banner: {
      sightName: String,
      bannerImg: String,
      gallaryImgs: Array
    }
  },
  components: {
    Gallary,
    FadeAnimation
  },
  data () {
    return {
      imgsShow: false
    }
  },
  methods: {
    handleBannerClick () {
      this.imgsShow = true
    },
    handleGallaryClose () {
      this.imgsShow = false
    }
  }
}
</script>

<style scoped lang="stylus">

  .banner
    height 0
    position relative
    background #eee
    overflow: hidden
    width 100%
    padding-bottom 55%
    .banner-img
      width 100%
    .banner-info
      display flex
      position absolute
      line-height .6rem
      left 0
      bottom 0
      right 0
      color: #fff
      background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8))
      .banner-title
        flex 1
        font-size: .32rem
        padding: 0 .2rem
      .banner-number
        height: .32rem
        line-height: .32rem
        margin-top: .14rem
        padding: 0 .4rem
        border-radius: .2rem
        background: rgba(0, 0, 0, .4)
        font-size: .24rem
        .banner-icon
          font-size .24rem

</style>
