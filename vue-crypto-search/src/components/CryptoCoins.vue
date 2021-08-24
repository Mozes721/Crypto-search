<template>
<div class="border-transparent rounded-lg text-center p-3 mx-auto -1/2 md:w-full my-2 bg-gradient text-black font-medium z-10 shadow-lg">
      <div class="py-4">Rank # {{cryptodata[1].rank}}
        <div id="annual" class="font-bold text-6xl">{{cryptodata[1].currency}}</div>
        <hr>
        <div class="text-sm my-3">&dollar; {{ cryptodata[1].price }} </div>
        <hr>
        <div class="text-sm my-3">Circulating Supply: {{ cryptodata[1].circulating_supply }} </div>
        <hr>
        <div class="text-sm my-3">Market Cap: {{ cryptodata[1].market_cap }} </div>
      </div>
    </div>   
</template>

<script>


export default {
 name: 'CryptoCoins',
 props: ['cryptodata'],
}
</script>

