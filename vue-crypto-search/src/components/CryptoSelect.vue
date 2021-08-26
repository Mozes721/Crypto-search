<template>
<section class="mx-auto -1/2 md:w-7/12">
    <br>
    <br>
    <div class="shadow flex">
    <input v-model="searched" class="w-full rounded p-2 bg-blue-50" type="text" placeholder="Search...">
    <button @click="onPress()" class="bg-red-400 hover:bg-red-300 rounded text-white p-2 pl-4 pr-4">
                <p class="font-semibold text-xs">Search</p>
    </button>
    
</div>
<br>
<h1 class="text-center font-mono text-6xl">Or</h1>
<br>
<select @change="onChange()"
  v-model="selected" class="form-select block w-full border p-3 rounded mt-10 bg-blue-50">
	<option value="0">Select your coin</option>
	<option v-for="crypto in cryptodata" :value="crypto.ID" :key="crypto.ID">{{crypto.name}}</option>
</select>
</section>
</template>

<script>
export default {
    name: 'CryptoSelect',
    props: ['cryptodata'],
    data () {
        return {
    searched: '',
	selected: 0
	}
    },
    methods: {
        onPress() {
            console.log(this.searched)
            if (this.cryptodata.find((item) => item.name.toLowerCase() === this.searched.toLowerCase())) {
                this.$emit('get-crypto', this.selected)
            }else {
                alert("Not found: " + this.searched)
            }
            this.searched = ''
        },
        onChange() {
            const coin = this.cryptodata.find((item) => item.name === this.selected)
            console.log(this.selected)
            console.log(coin)
            this.$emit('get-crypto', this.selected)
        }
    }
}
</script>
 
