<template>
  <chart v-if="info != null" v-bind:chartData="make_dataset(info)"/>  
</template>

<script>
import Chart from './components/chart.vue'
import axios from 'axios';

export default {
  name: 'App',
  data (){
    return {
      info: null
    }
  },
 methods: {
    make_dataset(json){
      json = Object.entries(json)

      var labels = json.map(function(e) {
        e = Object.entries(e)  
        return e[1][1].date;
      });
      var data = json.map(function(e) {
        e = Object.entries(e)  
        return e[1][1].sum;
      });

      var charData = {
            labels: labels,
            datasets: [{
               label: 'Graph Line',
               data: data,
               backgroundColor: 'rgba(0, 119, 204, 0.3)',
            }],
      };
      return charData
    }
  },
  mounted() {
    axios
      .get('http://localhost:8080/data.json')
      .then(response => (this.info = response.data));
  },
  components: {
    Chart
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
