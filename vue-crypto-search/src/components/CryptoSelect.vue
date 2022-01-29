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
<select v-model="selected"
 class="form-select block w-full border p-3 rounded mt-10 bg-blue-50">
	<option disabled value="">Select your Coin</option>
	<option v-for="crypto in cryptodata" v-bind:value="crypto.name" :key="crypto">{{crypto.name}}</option>
</select>
<span>Selected : {{selected}}</span>
</section>
</template>

<script>
export default {
    name: 'CryptoSelect',
    props: ['cryptodata', 'coinselect'],
    data () {
        return {
    searched: '',
    selected: ''
	}
    },
    methods: {
        onPress() {
            console.log(this.searched)
            if (this.cryptodata.find((item) => item.name.toLowerCase() === this.searched.toLowerCase())) {
                this.$emit('get-crypto', this.searched)
                
            }else {
                alert("Not found: " + this.searched)
            }
            this.searched = ''
        },
    },
    watch: {
        selected() {
            console.log(this.selected)
        }
    }
}
</script>