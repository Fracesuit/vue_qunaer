<template>
  <div class="wrapper">
    <swiper :options="swiperOption">
      <swiper-slide v-for="item in swiperSlides" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl"/>
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      },
      swiperSlides: [
        {
          id: '1',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1807/4f/37f83b87138a0c02.jpg_750x200_8e5df442.jpg'
        },
        {
          id: '2',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1807/4f/37f83b87138a0c02.jpg_750x200_8e5df442.jpg'
        }
      ]
    }
  }
}
</script>

<style lang="stylus" scoped>
  /*处理图片抖动问题，提前占位
  height 26.7%vw  有兼容性问题*/
  .wrapper >>> .swiper-pagination-bullet-active
    background #fff

  .wrapper
    overflow hidden
    background #eee
    width 100%
    height: 0
    padding-bottom 26.7%
    .swiper-img
      width 100%
</style>
