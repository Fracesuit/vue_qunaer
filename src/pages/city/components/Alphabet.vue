<template>
<ul class="list">
  <li class="item"  @click="handleLetterClick"
      @touchstart="handleTouchStart"
      @touchmove="handleTouchMove"
      @touchend="handleTouchEnd"
      v-for="item of letters"
      :ref="item"
      :key="item">{{item}}</li>
</ul>
</template>

<script>
export default {
  name: 'Alphabet',
  props: {
    cities: Object
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop
  },
  data () {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    }
  },
  methods: {
    handleLetterClick (data) {
      this.$emit('change', data.target.innerHTML)
    },
    handleTouchStart (e) {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          /* clientX：触摸目标在视口中的x坐标。
         clientY：触摸目标在视口中的y坐标。
         identifier：标识触摸的唯一ID。
         pageX：触摸目标在页面中的x坐标。
         pageY：触摸目标在页面中的y坐标。
         screenX：触摸目标在屏幕中的x坐标。
         screenY：触摸目标在屏幕中的y坐标。
         target：触目的DOM节点目标。 */
          const touchY = e.touches[0].clientY - 79
          const index = Math.floor((touchY - this.startY) / 20)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
    handleTouchEnd (e) {
      this.touchStatus = false
    }
  }
}
</script>

<style scoped lang="stylus">
  @import "~styles/varibles.styl"
    .list
      display flex
      flex-direction column
      justify-content center
      position absolute
      right 0
      bottom: 0
      top 1.58rem
      width .4rem
      .item
        text-align center
        color $bgcolor
        line-height .4rem
</style>
