<template>
  <div>
   <city-header></city-header>
    <city-seacher></city-seacher>
    <city-list></city-list>
  </div>
</template>

<script>
import CityHeader from './components/CityHeader'
import CitySeacher from './components/CitySeacher'
import CityList from './components/List'

export default {
  name: 'City',
  components: {
    CityHeader,
    CitySeacher,
    CityList
  }
}
</script>
