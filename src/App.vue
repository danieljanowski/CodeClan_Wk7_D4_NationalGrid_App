<template>
<div>
    <h1>Energy Mix in UK</h1>
  <div class="main_container">
      <energy-list  :energy_mix='energy_mix'></energy-list>
      <energy-chart :energy_chart='energy_chart'></energy-chart>
  </div>
  </div>
</template>

<script>
import EnergyList from './components/EnergyList.vue'
import EnergyChart from './components/EnergyChart.vue'

export default {
  name: 'app',
  data(){
    return {
      energy_mix:[],
      energy_chart:[]
    };
  },
  mounted(){
    fetch('https://api.carbonintensity.org.uk/generation')
    .then( data => data.json())
    .then( energy => this.energy_mix = energy.data)
  },
  computed:{
      format_data: function() {
        const generation = this.energy_mix.generationmix;    
        this.energy_chart.push(["Fuel", "Percentage"]);
        for (let item in generation) {
          let array = [];
          array.push(generation[item].fuel, generation[item].perc);
          this.energy_chart.push(array);
        }
    }
  },
  components:{
    "energy-list": EnergyList,
    "energy-chart": EnergyChart
  },
  methods:{
 
  },
}
</script>

<style scoped>
  h1{text-align: center;}
  /* .main_container{

  } */
  .energy-chart{
    padding: 0px;
  }
</style>