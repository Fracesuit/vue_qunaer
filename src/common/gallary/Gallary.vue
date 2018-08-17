<template>
<div class="gallary" @click="handleGallaryClick">
  <div class="wrapper">
    <swiper :options="swiperOption" >
      <swiper-slide v-for="(img,index) of imgs" :key="index">
        <img class="gallary-img" :src="img"/>
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</div>
</template>

<script>
export default {
  name: 'Gallary',
  props: {
    imgs: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observer: true,
        observeParents: true
      }
    }
  },
  methods: {
    handleGallaryClick () {
      this.$emit('handleGallaryClick')
    }
  }
}
</script>

<style scoped lang="stylus">
  .gallary >>> .swiper-container
    overflow inherit
  .gallary
    z-index 99
    background #000
    position fixed
    display  flex
    flex-direction column
    justify-content center
    left 0
    bottom 0
    top 0
    right 0
    .wrapper
      height: 0
      width: 100%
      padding-bottom: 100%
      .gallary-img
        width 100%
      .swiper-pagination
        color: #fff
        bottom: -1rem
</style>
