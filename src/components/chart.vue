<template>
  <Bar v-bind:chartData="chartData" />
  <strong>{{chartData}}</strong>
</template>

<script>

import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'Chart',
        extends: Bar,
    props: ['chartData'],
  components: {
    Bar
  },
}
</script>

<style scoped>
</style>
