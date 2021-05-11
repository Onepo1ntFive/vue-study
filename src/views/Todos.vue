<template>
    <div>
        <h2>Todo list</h2>
        <AddTodo @add-todo="addTodo" />
        <TodoList v-bind:todos="todos" @remove-todo="removeTodo" />
        <p><router-link to="/">Main page</router-link></p>
    </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddTodo from "@/components/AddTodo";
export default {
    name: "App",
    components: {
        TodoList: TodoList,
        AddTodo: AddTodo,
    },
    data() {
        return {
            todos: [],
        };
    },
    mounted() {
        fetch("https://jsonplaceholder.typicode.com/todos?_limit=5")
            .then((response) => response.json())
            .then((json) => (this.todos = json));
    },
    methods: {
        removeTodo(id) {
            this.todos = this.todos.filter((todo) => todo.id !== id);
        },
        addTodo(todo) {
            this.todos.push(todo);
        },
    },
};
</script>
