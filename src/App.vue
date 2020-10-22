<template lang='html'>
	<div>
		<h1>Energy Tracker</h1>
		<energy-list :fuelData='fuelData'></energy-list>
		<energy-chart :fuelData='fuelData'></energy-chart>
	</div>
</template>

<script>
import EnergyMix from './components/EnergyMix.vue';
import EnergyChart from './components/EnergyChart.vue'

export default {
	name: 'app',
	data(){
		return {
			fuelData: [], 
		}
	},
	mounted () {
        fetch ('https://api.carbonintensity.org.uk/generation')
        .then (response => response.json())
        .then (json => this.fuelData = json.data.generationmix);
	}, 
	components:{
		"energy-list" : EnergyMix,
		"energy-chart": EnergyChart
	}
}

</script>

<style lang="css" scoped>
h1{
	font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

</style>