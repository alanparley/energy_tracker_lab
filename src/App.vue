<template lang='html'>
	<div>
		<h1>Energy Tracker</h1>
		<energy-list :fuelData='fuelData'></energy-list>

		<GChart
			type="Col"
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
				['Year', 'Sales', 'Expenses', 'Profit'],
				['2014', 1000, 400, 200],
				['2015', 1170, 460, 250],
				['2016', 660, 1120, 300],
				['2017', 1030, 540, 350]
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