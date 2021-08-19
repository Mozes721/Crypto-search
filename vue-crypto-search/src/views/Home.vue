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
    
      const res = await fetch('https://api.nomics.com/v1/currencies/ticker?key=098b31cf28f6a5c39e2daffaff3e9809e41d435d')
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
