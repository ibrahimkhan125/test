<template>
 <div id="app">
  {{msg}}
  <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" /> 
 </div>  
 

</template>

<script>
import Todos from './components/Todos';
export default {
  name: 'App',
  components: {
    Todos
  },
  methods:{
    deleteTodo(id){
      console.log('herllo', id)
    },  
  },  
  data() {
    return {
      todos : [
        {
          id: 1,
          title: 'todo One',
          completed: false
        },
        {
          id: 2,
          title: 'todo Two',
          completed: true
        },
        {
          id: 3,
          title: 'todo Three',
          completed: false
        }
      ]
    }
  }
}
</script>

<style>
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body{
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
