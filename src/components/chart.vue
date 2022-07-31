<template>
        <button class="rm" v-on:click="fill_info(chartData)">&times;</button>
    <strong>{{chartData}}</strong>
<Bar v-bind:chartData="chartData"

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
    props: ['chartData'],
  /*props: {
    todos: ['todos'],
    chartData1: ['chartData1'],
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
      default: 600
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
*/
  components: {
    Bar
  },
 /* data (){
    return{ "chartData": { "labels": [ "2022-06-07"], "datasets": [ { "label": "Graph Line", "data": [ "67804"] } ] }, "chartOptions": { "type": "bar", "responsive": false, "maintainAspectRatio": false } }
  },*/
  methods: {
    fill_info(chartData){
      this.info=this.info+1;
      chartData = Object.entries(chartData)
      alert(chartData);
    }
  }
}

</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
