<template>
  <!--strong>{{info}}</strong-->
  <!--chart v-bind:chartData="info"/-->  
  <!--chart v-bind:chartData="info"/-->  
  <chart v-if="info != null" v-bind:chartData="make_dataset(info)"/>  
  <!--todo v-bind:todos="make_dataset(info)"/-->
  <!--todo v-bind:todos="make_dataset(info)"/-->
</template>

<script>
import Todo from './components/todo.vue'
import Chart from './components/chart.vue'

import axios from 'axios';

export default {
  name: 'App',
 

  data (){
    return {
      info: null

//      {"0":{"date":"2022-06-07","sum":"67804"},"1":{"date":"2022-06-08","sum":"89440"},"2":{"date":"2022-06-09","sum":"102223"},"3":{"date":"2022-06-10","sum":"116272"},"4":{"date":"2022-06-11","sum":"217936"},"5":{"date":"2022-06-12","sum":"173255"},"6":{"date":"2022-06-13","sum":"143888"},"7":{"date":"2022-06-14","sum":"110311"},"8":{"date":"2022-06-15","sum":"112741"},"9":{"date":"2022-06-16","sum":"144709"},"10":{"date":"2022-06-17","sum":"114865"},"11":{"date":"2022-06-18","sum":"187083"},"12":{"date":"2022-06-19","sum":"131443"},"13":{"date":"2022-06-20","sum":"114614"},"14":{"date":"2022-06-21","sum":"114380"},"15":{"date":"2022-06-22","sum":"137649"},"16":{"date":"2022-06-23","sum":"131337"},"17":{"date":"2022-06-24","sum":"138427"},"18":{"date":"2022-06-25","sum":"216804"},"19":{"date":"2022-06-26","sum":"150335"},"20":{"date":"2022-06-27","sum":"126523"},"21":{"date":"2022-06-28","sum":"97676"},"22":{"date":"2022-06-29","sum":"107060"},"23":{"date":"2022-06-30","sum":"109308"},"24":{"date":"2022-07-01","sum":"147775"},"25":{"date":"2022-07-02","sum":"209482"},"26":{"date":"2022-07-03","sum":"158427"},"27":{"date":"2022-07-04","sum":"113595"},"28":{"date":"2022-07-05","sum":"170066"},"29":{"date":"2022-07-06","sum":"182935"},"30":{"date":"2022-07-07","sum":"110508"}}

    }
  },
 methods: {
    make_dataset(json){

if(json != null){

json = Object.entries(json)
//  alert(json)

var labels = json.map(function(e) {
e = Object.entries(e)  
//  alert(e[1][1].date)
   return e[1][1].date;
});
var data = json.map(function(e) {
e = Object.entries(e)  
//  alert(e[1][1].date)
   return e[1][1].sum;
});

/*
var config = {
   type: 'bar',
   data: {
      labels: labels,
      datasets: [{
         label: 'Graph Line',
         data: data,
         backgroundColor: 'rgba(0, 119, 204, 0.3)'
      }]
   }
};*/
var config = {
//   chartData: {
      labels: labels,
      datasets: [{
         label: 'Graph Line',
         data: data
      }],
//   },
   chartOptions: {
        type: 'bar',
        responsive: false,
        maintainAspectRatio: false
      }
};



}

      return config
    }
  },
  mounted() {

    axios
      .get('http://localhost:8080/data.json')
      .then(response => (this.info = response.data));
//alert('ffff');
  },
  components: {
  Todo, Chart
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
