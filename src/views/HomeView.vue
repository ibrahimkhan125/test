<template>
  <div id="app">
   
   <AddTodo v-on:add-todo="addTodo"/>
   <Todos v-bind:todos="todos" v-on:del-todo1="deleteTodo" /> 
  </div>  
  
 
 </template>
 
 <script>
 import Todos from '../components/Todos';
 
 import AddTodo from '../components/AddTodo';
 import axios from 'axios';
 export default {
   name: 'HomeView',
   components: {
     Todos,
     AddTodo
   },
   methods:{
     deleteTodo(id){
       axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
       .then(this.todos = this.todos.filter(todo => todo.id != id))
       .catch(err => console.log(err));
       // this.todos = this.todos.filter(todo => todo.id != id)
     },  
     addTodo(newTodo){
       const {title, completed} = newTodo; 
       axios.post('https://jsonplaceholder.typicode.com/todos', {
         title,
         completed
       })
       .then(res => this.todos = [...this.todos, res.data])
       .catch(err => console.log(err));
       // this.todos.push(newTodo);
       // console.log('parent', newTodo);
     }
   },  
   data() {
     return {
       todos : []
     }
   }, 
   created(){
     axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
     .then(res => this.todos = res.data)
     .catch(err => console.log(err));
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
 .btn{
   display: inline-block;
   border: none;
   background: #555;
   color:#fff;
   padding: 7px 20px;
   cursor: pointer;
 }
 .btn:hover{
   background: #666;
 }
 p{
  text-align: left;
 }
 </style>
 