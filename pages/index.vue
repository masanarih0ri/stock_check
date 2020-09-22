<template>
  <div>
    <header>ヘッダー</header>
    <div v-if="stocksInfo">
      {{stocksInfo}}
    </div>
  </div>
</template>

<script>
// import Logo from '~/components/Logo.vue'
import axios from 'axios'

export default {
  data() {
    return {
      stocksInfo: null
    }
  },
  mounted() {
    axios
    .get(`http://localhost:3000/api/tiingo/daily/fsly/prices?token=${process.env.API_KEY}`)
    .then(response => (this.stocksInfo = response.data));
  }
}
</script>

<style>
</style>
