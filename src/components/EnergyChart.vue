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
    name: 'energy-chart',
    data(){
        return {
			chartOptions:{
                width: 1400,
                height: 700,
                is3D: true,
                backgroundColor: {
                    stroke: 'black',
                    strokeWidth: 5,
                },
                chartArea:{
                    width: "75%",
                    height: "80%"
                }, 
                legend:{
                    position: 'top', 
                    alignment: 'center'
                }
			}
        }
    }, 
    components:{
        GChart
    }, 
    props: ['fuelData'], 
    computed:{
        chartData: function(){
            let chartData = [['Fuel Type', 'Percentage']];
            for (const energy of this.fuelData){
                chartData = [...chartData, [energy.fuel.toUpperCase(), energy.perc]]
            }
            return chartData
        }
    }
}
</script>

<style lang="css" scoped>

div{
    display: flex;
    justify-content: center;    

}

</style>