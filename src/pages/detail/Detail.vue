<template>
    <div class="container">
      <banner :banner="banner"></banner>
      <detail-header></detail-header>
      <detail-list :list="list"></detail-list>
    </div>
</template>

<script>
import Banner from './components/Banner'
import DetailHeader from './components/DetailHeader'
import DetailList from './components/List'
import axios from 'axios'
export default {
  name: 'Detail1',
  components: {Banner, DetailHeader, DetailList},
  methods: {
    getDetailInfo: function () {
      // axios.get('/api/detail.json?id=' + this.id)
      axios.get('/api/detail.json?', {
        params: {
          id: this.$route.params.id
        }
      }).then(this.getDetailInfoSucc)
    },
    getDetailInfoSucc (res) {
      const resData = res.data
      if (resData.ret && resData.data) {
        const data = resData.data
        this.list = data.categoryList
        this.banner.sightName = data.sightName
        this.banner.bannerImg = data.bannerImg
        this.banner.gallaryImgs = data.gallaryImgs
      }
    }
  },
  mounted () {
    this.getDetailInfo()
  },
  data () {
    return {
      id: '',
      lastId: '',
      list: [],
      banner: {
        sightName: '',
        bannerImg: '',
        gallaryImgs: []
      }
    }
  }
}
</script>

<style scoped lang="stylus">
  .container
    height 50rem
</style>
