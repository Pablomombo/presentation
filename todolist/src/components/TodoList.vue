<template>
    <div class="hello">
        <input type="text" class="todo" placeholder="you have to do it"
        v-model="newTodo" @keyup.enter="addTodo">
        <h1>{{ msg }}</h1>
        <div v-for="todo in todos" :key="todo.id" class="todo-item">
            <div :class="{ completed : todo.completed}">
                <input type="checkbox" v-model="todo.completed">
                {{ todo.title }}
            </div>
        </div>
        <div class="all">
            <input type="submit" @click="removeTodo" value="Delete"/>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TodoList',
    data() {
        return {
            msg: 'Welcome to my todo list',
            newTodo: '',
            idForTodo: '',
            todos: [],
        }
    },
    methods: {
        addTodo() {
            this.todos.push({
                id: this.idForTodo,
                title: this.newTodo,
                completed: false,
            })
            this.newTodo = ''
            this.idForTodo++
        },      
        removeTodo() {
            this.todos = this.todos.filter (function (todo){
                return !todo.completed;
            })
        }
    }
}
</script>

<style>
.todo {
    width: 100%;
    padding: 10px 18px;
    font-size: 18px;
    margin-bottom: 16px;
}
h1 {
    text-align: center;
}
.todo-item {
    font-size: 22px;
}
.remove {
    cursor: pointer;
    margin-left: 14px;
}
.completed {
    text-decoration: line-through;
    color: black;
}
.all {
    padding-top: 10px;
    border-top: 1px solid grey;
}
</style>