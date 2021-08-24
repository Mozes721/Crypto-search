<template>
<select v-model="selected" class="form-select block w-full border p-3 rounded mt-10 bg-blue-50">
	<option value="0">Select your coin</option>
	<option v-for="crypto in cryptodata" :value="crypto.ID">{{crypto.name}}</option>
</select>
</template>

<script>
export default {
    name: 'CryptoSelect',
    props: ['cryptodata'],
    data () {
        return {
	selected: 0
	}
    }
}
</script>
 
