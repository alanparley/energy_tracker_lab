<template>
<div>
    <GChart
    type="PieChart"
    :data="chartData"
    :options="chartOptions"
    />
</div>
</template>

<script>
import { GChart } from 'vue-google-charts'
export default {
    data(){
        return {
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
    components:{
        GChart
    }, 
    props: ['fuelData']
}
</script>

<style>

</style>