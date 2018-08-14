<template>
  <div>
    <div class="title">热销推荐</div>
    <ul>
      <li class="item" v-for="recommend of list" :key="recommend.id">
        <img class="item-img" :src="recommend.imgUrl">
        <div class="item-info">
          <p class="item-title">{{recommend.title}}</p>
          <p class="item-desc">{{recommend.desc}}</p>
          <button class="item-button">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Recommend',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/mixins.styl'
  .title
    background #eee
    margin-top .2rem
    line-height .8rem
    text-indent .2rem
  .item
    overflow hidden
    display flex
    height 1.9rem
    .item-img
      width 1.7rem
      height 1.7rem
      margin .1rem
    .item-info
      flex 1
      min-width 0
      padding .1rem
      .item-title
        line-height .54rem
        font-size .32rem
        ellipse()
      .item-desc
        line-height .4rem
        color #ccc
        ellipsis()
      .item-button
        color #fff
        margin-top .16rem
        line-height .44rem
        padding 0 .2rem
        border-radius .06rem
        background #ff9300
</style>
