<template>
    <div class="todo">
        <!-- <h1>Todos</h1> -->
        <div  v-for='todo in todos' v-bind:key="todo.id">
            <!-- {{todo.title}} -->
            <TodoItem v-bind:todoP="todo" v-on:del-todo="$emit('del-todo1', todo.id)" />
        </div>
         
    </div>
</template>
<script>
import TodoItem from './TodoItem.vue';
export default {
    name: "TodoS",
    props: ['todos'],
    components: {
        TodoItem
    }
}
</script>
<style scoped>
.todo{
    padding: 20px;
}
</style>