<template>
  <div>
      <ul v-if="fuelData">
          <li v-for="(energy, index) in fuelData" :energy="energy" :key="index">
              <h2>{{ energy.fuel.toUpperCase() }}</h2>
              <p>{{ energy.perc }}%</p>
          </li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'energy-list',
    props: ['fuelData'],
}
</script>

<style lang="css" scoped>
li{
    font-family: Arial, Helvetica, sans-serif;
    list-style-type: none;
    box-shadow: 10px 10px 5px rgb(158, 158, 158);
    border: 3px solid black;
    border-radius: 20px;
    padding: 10px;
    min-width:120px;
    max-width:120px;
    margin:20px;
}
ul{
    display: flex;
    justify-content: flex-start;
    flex-wrap: wrap;
    padding:20px;
    margin: 0;
}

</style>