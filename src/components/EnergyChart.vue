<template>
<div class="chart">
    <GChart
    type="PieChart"
    :data="energy_chart"
    :options="chartOptions"
    style="width: 900px; height: 500px;"
  />
  </div>
</template>

<script>
import { GChart } from 'vue-google-charts'
 
export default {
  props: ['energy_chart'],
  components: {
    GChart
  },
  data () {
    return {
      // Array will be automatically processed with visualization.arrayToDataTable function
      chartOptions: {
         is3D: true,
        chart: {
           
            title: 'Energy Mix Pie Chart',
            subtitle: 'fuel percentage',
        }
      }
    }
  }
}
</script>

<style scoped>
  .chart{

  }

</style>