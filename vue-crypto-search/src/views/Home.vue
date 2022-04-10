<template>
  <main v-if="!loading">
    <CryptoCoin v-bind:cryptocoin="cryptocoin" />
  
    <CryptoSelect @get-crypto="getCryptoData" v-bind:cryptodata="cryptodata"/>
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
        loading: true, 
        name: 'Bitcoin',
        cryptodata: [],
        cryptocoin: [],
        loadingImage: require('../assets/super-buu-hourglass.gif')
      }
    },
  methods: {
    async fetchCryptoData() {
      const res = await fetch('https://api.nomics.com/v1/currencies/ticker?key=yourAPIKey')
      const data = await res.json()
      return data
     
    },
    getCryptoData(crypto) {
      
      this.loading = true

      this.name = crypto
      this.cryptocoin = this.cryptodata.find(coin => coin.name === this.name)
      setInterval(this.updateCryptoData, 3000);
      
      
      
    },
    updateCryptoData() {
      console.log(`Printed crypto after 3 seconds`)
      
      this.loading = false
    }
  },
    async created() {
      const data = await this.fetchCryptoData()
      this.cryptodata = data
      this.cryptocoin = this.cryptodata.find(coin => coin.name === this.name)
      this.loading = false
    },
}
</script>
