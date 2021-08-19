<template>
  <div class="home">
    Hell Crypto
    
  </div>
</template>

<script>
export default {
  name: 'Home',
  components: {},
  data() {
      return {
        loading: true,
        currency: 'BTC',
        logo_url : '',
        
      }
    },
  methods: {
    async fetchCryptoData() {
    
      const res = await fetch('https://api.nomics.com/v1/currencies/ticker?key=your_api_key')
      const data = await res.json()
      return data
    }
  },
    async created() {
      const data = await this.fetchCryptoData()
      console.log(data)
      .then(response => (this.crypto = response))
    },
}

</script>
