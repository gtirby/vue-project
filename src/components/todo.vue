<template>
<div>
      <button class="rm" v-on:click="fill_info()">&times;</button>

  <ul v-for="todo of todos">
    <!--TodoItem 
      v-for="todo of todos"
      v-bind:todo="todo" 
    /-->

    <li>{{todo.date}} -- {{todo.sum}}</li>
  </ul>
    <strong>{{info}}</strong>
   <strong>{{todo}}</strong>

</div>
</template>

<script>

//import TodoItem from './todo_item.vue'

export default {
  name: 'Todo',
  props: ['todos'],
  components: {
 //   TodoItem
  },
  data (){
    return{
    info: 0
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
