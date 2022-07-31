<template>

  <li>
    <span>
      <input type="checkbox" name="">
      <strong>{{todo.id}}</strong>
      {{todo.title}}  
    </span>
    <button class="rm" v-on:click="">&times;</button>
    </li>

</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todo']
}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
