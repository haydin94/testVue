<template>
    <div id="todos">
        <AddTodo v-on:add-todo="addTodo" v-bind:max-id="maxId"></AddTodo>
        <div v-bind:key="todo.id" v-for="todo in todos">
            <Item v-bind:todo="todo" v-on:delete-todo="$emit('delete-todo', todo.id)"></Item>
        </div>

    </div>

</template>

<script>
    import Item from './Item'
    import AddTodo from "./AddTodo";

    export default {
        name: "Todos",
        props: ["todos", "maxId"],
        components: {
            AddTodo,
            Item
        },
        methods: {
            addTodo(newTodo) {
                this.todos.push(newTodo);
            }
        }
    }
</script>

<style scoped>
    #todos {
        padding-right: 50%;
    }


</style>