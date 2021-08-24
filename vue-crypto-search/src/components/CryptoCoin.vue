<template>
<div class="border-transparent rounded-lg text-center p-3 mx-auto -1/2 md:w-7/12 my-2 bg-gradient text-black font-medium z-10 shadow-lg bg-indigo-300">
      <div class="py-4">Rank # {{cryptodata[0].rank}}
        <img class="mx-auto py-px h-20" v-bind:src="cryptodata[0].logo_url">
        <div id="annual" class="font-bold text-6xl">{{cryptodata[0].currency}}</div>
        <hr>
        <div class="text-sm my-3">Price: &dollar; {{ cryptodata[0].price }} </div>
        <hr>
        <div class="text-sm my-3">Circulating Supply: {{ cryptodata[0].circulating_supply }} </div>
        <hr>
        <div class="text-sm my-3">Market Cap: {{ cryptodata[0].market_cap }} </div>
      </div>
    </div>   
</template>

<script>


export default {
 name: 'CryptoCoins',
 props: ['cryptodata'],
}
</script>

