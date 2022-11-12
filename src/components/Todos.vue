<template>
    <div>
        <h1>Todos</h1>
        <div v-for='todo in todos' v-bind:key="todo.id">{{todo.title}}</div> 
    </div>
</template>
<script>
export default {
    name: "TodoS",
    props: ['todos']
}
</script>
<style scoped>
</style>