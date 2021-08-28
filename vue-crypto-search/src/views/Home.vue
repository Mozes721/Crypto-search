<template>
  <main v-if="!loading">
    <CryptoCoin :cryptocoin="cryptocoin" />
  
    <CryptoSelect @get-crypto="getCryptoData" :cryptodata="cryptodata"/>
  </main>

  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-gray-600 text-4xl mt-9 mb-5">
      Fetching Data
    </div>
    <img :src="loadingImage" class="w-30 m-auto" alt="searching" />
  </main>
</template>

<script>
import CryptoCoin from '@/components/CryptoCoin'
import CryptoSelect from '@/components/CryptoSelect'
export default {
  name: 'Home',
  components: {
    CryptoCoin,
    CryptoSelect
  },
  data() {
      return {
        loading: false,
        name: 'Bitcoin',
        cryptodata: [],
        cryptocoin: [],
        loadingImage: require('../assets/super-buu-hourglass.gif')
      }
    },
  methods: {
    async fetchCryptoData() {
      const res = await fetch('https://api.nomics.com/v1/currencies/ticker?key=ba659a90cd165d860bb631048dd09e1fab4a2f47')
      const data = await res.json()
      return data
     
    },
    getCryptoData(crypto) {
      this.cryptodata = data[crypto]
    }
  },
    async created() {
      const data = await this.fetchCryptoData()
      this.cryptodata = data
      this.cryptocoin = data.find(coin => coin.name === this.name)
      // this.cryptoSearched = data
      // this.currency = data.currency
      // this.logo_url = data.logo_url
      // this.stats = data.id
      // this.price = data.price
      // this.circulating_supply = data.circulating_supply
      // this.market_cap = data.market_cap
    },
}
</script>