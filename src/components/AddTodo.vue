<template>
    <div>
        <form v-on:submit.prevent="addTodo">
            <input type="text" name="title" v-model="title" id="" placeholder="Add Todo...">
            <input class="btn" type="submit" value="Submit">
        </form>
    </div>
</template>    
<script>
// import * as uuid from 'uuid';
    export default {
        name: "AddTodo",
        data(){
            return {
                title: ''                
            }
        },
        methods: {
            addTodo() {
                const newTodo = {
                    // id: uuid.v4(),
                    title: this.title,
                    completed: false
                }
                //send to parent
                this.$emit('add-todo', newTodo);
                this.title = '';
            }
        }
    }
</script>
<style scoped>
    form{
        display: flex;
    }
    input[type='text'] {
        flex: 10;
        padding: 5px;
    }
     
</style>