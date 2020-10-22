<template lang='html'>
	<div>
		<h1>UK Energy Tracker</h1>
		<h2>Time Frame: {{this.timeFrameFrom.slice(0,10)}} @ {{this.timeFrameFrom.slice(11,16)}} to {{this.timeFrameTo.slice(0,10)}} @ {{this.timeFrameTo.slice(11,16)}} </h2>
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
			timeFrameFrom: "",
			timeFrameTo: ""
		}
	},
	mounted () {
        fetch ('https://api.carbonintensity.org.uk/generation')
        .then (response => response.json())
		.then (json => {
			this.fuelData = json.data.generationmix
			this.timeFrameFrom = json.data.from
			this.timeFrameTo = json.data.to
			}
		)
	}, 
	components:{
		"energy-list" : EnergyMix,
		"energy-chart": EnergyChart
	}
}

</script>

<style lang="css" scoped>
h1{
	text-align: center;
	font-size: 56px;
	margin: 10px;
}

h2{
	font-weight: normal;

}

div{
	text-align: center;
	font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

</style>