<template>
  <div>
   <city-header></city-header>
    <city-seacher :cities="cities"></city-seacher>
    <city-list :cities="cities" :hot="hotCities" :letter="letter"></city-list>
    <city-alphabet :cities="cities" @change="handleLetterClick"></city-alphabet>
  </div>
</template>

<script>
import CityHeader from './components/CityHeader'
import CitySeacher from './components/CitySeacher'
import CityList from './components/CityList'
import CityAlphabet from './components/Alphabet'
import axios from 'axios'
export default {
  name: 'City',
  components: {
    CityHeader,
    CitySeacher,
    CityList,
    CityAlphabet
  },
  data () {
    return {
      cities: {},
      hotCities: [],
      letter: ''
    }
  },
  methods: {
    getCity () {
      axios.get('/api/city.json')
        .then(this.getgetCitySucc)
    },
    getgetCitySucc: function (res) {
      const resData = res.data
      if (resData.ret && resData.data) {
        const data = resData.data
        this.cities = data.cities
        this.hotCities = data.hotCities
      }
    },
    handleLetterClick (data) {
      this.letter = data
    }
  },
  mounted () {
    this.getCity()
  }
}
</script>
