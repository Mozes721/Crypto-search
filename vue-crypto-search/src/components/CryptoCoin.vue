<template>
<div class="border-transparent rounded-lg text-center p-3 mx-auto -1/2 md:w-7/12 my-2 bg-gradient text-black font-medium z-10 shadow-lg bg-indigo-400">
      <div class="py-4">Rank # {{cryptocoin.rank}}
        <img class="mx-auto py-px h-20" v-bind:src="cryptocoin.logo_url">
        <div id="annual" class="font-bold text-6xl">{{cryptocoin.name}}</div>
        <div id="annual" class="font-bold text-6xl">{{cryptocoin.currency}}</div>
        <hr>
        <div class="text-sm my-3">Price: &dollar; {{ cryptocoin.price }} </div>
        <hr>
        <div class="text-sm my-3">Circulating Supply: {{ cryptocoin.circulating_supply }} </div>
        <hr>
        <div class="text-sm my-3">Market Cap: {{ cryptocoin.market_cap }} </div>
      </div>
    </div>   
</template>

<script>


export default {
 name: 'CryptoCoins',
 props: ['cryptocoin'],
}
</script>

