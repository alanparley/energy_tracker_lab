<template lang='html'>
	<div>
		<h1>Energy Tracker</h1>
		<energy-list :fuelData='fuelData'></energy-list>
	</div>
</template>

<script>
import EnergyMix from './components/EnergyMix.vue';

export default {
	name: 'app',
	data(){
		return {
			fuelData: []
		}
	},
	mounted () {
        fetch ('https://api.carbonintensity.org.uk/generation')
        .then (response => response.json())
        .then (json => this.fuelData = json.data.generationmix);
	}, 
	components:{
		"energy-list" : EnergyMix
	}
}

</script>

<style lang="css" scoped>
h1{
	font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

</style>