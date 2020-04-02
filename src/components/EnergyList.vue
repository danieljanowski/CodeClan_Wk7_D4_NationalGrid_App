<template>
<div>
  <h1>Energy share:</h1>
  <p>{{energy_mix.from.slice(0,10)}}  at {{energy_mix.from.slice(11,16)}}</p>
  <ul>
      <li v-for="energy in energy_mix.generationmix">{{energy.fuel}}: {{energy.perc}}%</li>
  </ul>
</div>
</template>

<script>
export default {
    name:'energy-list',
    props:['energy_mix']
}
</script>

<style scoped>

</style>