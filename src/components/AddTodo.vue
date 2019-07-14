<template>
    <div class="add-todo">
        <form @submit="addTodo" onsubmit="return false">
            <a>Input: </a>
            <input type="text" name="title" v-model="title" placeholder="Add Todo.." v-on:submit="addTodo"/>
            <input type="submit" value="Submit"/>
        </form>
    </div>
</template>

<script>
    export default {
        name: "AddTodo",
        props: ["maxId"],
        methods: {
            addTodo() {
                const newTodo = {
                    id: ++this.maxId,
                    title: this.title,
                    completed: false
                };
                // send up to parent. U can do it also in template
                this.$emit('add-todo', newTodo);
            }
        },
        data(){
            return{
                title: ''
            }
        }
    }
</script>

<style scoped>
    .add-todo{
        border: 1px gray;
        background: whitesmoke;
        padding: 5px;
    }
    form {
        display: flex;
        align-items: center;
    }

    input[type="text"] {
        flex: 10;
        margin-left: 5px;
        padding: 5px;
        background: whitesmoke;
        border-radius: 1%;
        border: inherit solid 1px;
    }

    input[type="submit"] {
        flex: 2;
        margin-left: 2px;
        padding: 0;
    }
</style>