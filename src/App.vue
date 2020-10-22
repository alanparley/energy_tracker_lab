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

</style>