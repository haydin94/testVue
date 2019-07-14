<template>
    <div id="app">
        <Header></Header>
        <Todos v-bind:todos="todos" v-bind:max-id="maxId" v-on:delete-todo="deleteTodo"></Todos>
        <p>{{ maxId }}</p>
    </div>
</template>

<script>
    import Header from './components/Header/Header'
    import Todos from './components/Todos'

    export default {
        name: 'app',
        components: {
            Header,
            Todos
        },

        data() {
            return {
                todos: [
                    {
                        id: 1,
                        title: 'Todo One',
                        completed: false
                    },
                    {
                        id: 2,
                        title: 'Todo two',
                        completed: false
                    },
                    {
                        id: 3,
                        title: 'Todo three',
                        completed: false
                    }
                ]
            }
        },

        computed: {
            maxId: {
                get: function () {
                    let max = 0;
                    for (let i = 0; i < this.todos.length; i++) {
                        if(this.todos[i].id > max)
                            max = this.todos[i].id;
                    }
                    return max;
                    // return Math.max(this.todos.map(x => x.id), 0);

                },
                set: function(newValue){
                    return newValue;
                }
            }
        },

        methods: {
            deleteTodo(id) {
                this.todos = this.todos.filter(todo => todo.id !== id)
            }
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 10px;
    }
</style>
