<template>
 <div class="grid grid-cols-1 gap-3">
    <div class="shadow-md bg-blue-200 p-10 text-center rounded">
    <h3>Coin</h3>
    {{ cryptodata[1].currency }}
    {{ cryptodata[1].price }}
    {{ cryptodata[1].circulating_supply }}
    {{ cryptodata[1].market_cap }}
    </div> 
 </div>
</template>

<script>


export default {
 name: 'CryptoCoins',
 props: ['cryptodata'],
}
</script>

