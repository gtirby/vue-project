<template>
<Bar
    :chart-options="chartOptions"
    :chart-data="chartData"
    :chart-id="chartId"
    :dataset-id-key="datasetIdKey"
    :plugins="plugins"
    :css-classes="cssClasses"
    :styles="styles"
    :width="width"
    :height="height"
  />
</template>

<script>

import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

//import TodoItem from './todo_item.vue'

export default {
  name: 'Chart',
        extends: Bar,
  props: {
    chartId: {
      type: String,
      default: 'bar-chart'
    },
    datasetIdKey: {
      type: String,
      default: 'label'
    },
    width: {
      type: Number,
      default: 400
    },
    height: {
      type: Number,
      default: 400
    },
    cssClasses: {
      default: '',
      type: String
    },
    styles: {
      type: Object,
      default: () => {}
    },
    plugins: {
      type: Object,
      default: () => {}
    }
  },

  components: {
    Bar
  },
  data (){
    return{
      chartData: {
        labels: [
      'January',
      'February',
      'March',
      'April',
      'May',
      'June',
      'July',
      'August',
      'September',
      'October',
      'November',
      'December'
    ],
            datasets: [
      {
        label: 'Data One',
        data: [40, 20, 12, 39, 10, 40, 39, 8, 40, 20, 12, 11]
      }]
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false
      }
  }
  },
  methods: {
    fill_info(){
      this.info=this.info+1;
 //     alert('getTime()');
    }
  }
}

</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
