<template>
  <div>
      <ul v-if="fuelData">
          <li v-for="(energy, index) in fuelData" :energy="energy" :key="index">
              <h2>{{ energy.fuel }}</h2>
              <p>{{ energy.perc }} %</p>
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
    list-style-type: none;
}
</style>