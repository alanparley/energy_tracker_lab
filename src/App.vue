<template lang='html'>
	<div>
		<h1>Energy Tracker</h1>
		<energy-list :fuelData='fuelData'></energy-list>

		<GChart
			type="PieChart"
			:data="chartData"
			:options="chartOptions"
  		/>
	</div>
</template>

<script>
import EnergyMix from './components/EnergyMix.vue';
import { GChart } from 'vue-google-charts'

export default {
	name: 'app',
	data(){
		return {
			fuelData: [], 
			chartData: [
				['Fuel Type', 'Percentage'],
				['Biomass', 20],
				['Wind', 30],
				['Gas', 50]
			],
			chartOptions:{
				chart:{
					title: 'Company Performance',
          			subtitle: 'Sales, Expenses, and Profit: 2014-2017',
				}
			}
		}
	},
	mounted () {
        fetch ('https://api.carbonintensity.org.uk/generation')
        .then (response => response.json())
        .then (json => this.fuelData = json.data.generationmix);
	}, 
	components:{
		"energy-list" : EnergyMix,
		GChart
	}
}

</script>

<style lang="css" scoped>
h1{
	font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

</style>