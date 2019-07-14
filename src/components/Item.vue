<template>
    <div class="item">
        <a class="text">Item</a>
        <a class="text">{{todo.id}}: </a>
        <a class="text" v-bind:class="{'is-complete':todo.completed}">{{todo.title}}</a>
        <input type="checkbox" v-on:change="markComplete">
        <button class="delete" @click="$emit('delete-todo', todo.id)">x</button>
    </div>
</template>

<script>
    export default {
        name: "Item",
        props: {
            todo: {
                type: Object,
                required: true
            },
            iwas: {
                required: false
            }
        },
        methods: {
            markComplete() {
                this.todo.completed = !this.todo.completed;
            }
        }
    }
</script>

<style scoped>
    .item {
        background: gray;
        border-bottom: black solid 1px;
        padding: 10px;
    }

    .text {
        padding-left: 2px;
    }

    .is-complete {
        text-decoration: line-through;
    }

    .delete {
        background: red;
        color: aliceblue;
        border: none;
        padding: 3px 5px;
        border-radius: 55%;
        cursor: pointer;
        margin-left: 10%;
        float: right;
    }
</style>