<template>
    <li>
        <span v-bind:class="{ done: todo.completed}">
            <input type="checkbox" v-on:change="todo.completed = !todo.completed">
            <strong>{{ index + 1 }}</strong>
            {{ todo.title }}
        </span>
        <button class="rm" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
    </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            requared: true,
        },
        index: Number
    },
};
</script>

<style scoped>
    li {
        padding: 0.5rem 2rem;
        margin-bottom: 1rem;
        border: 1px solid #ccc;
        display: flex;
        justify-content: space-between;
    }
    input {
        margin-right: 0.5rem;
    }
    .rm {
        border: 0;
        background: #f00;
        color: #fff;
        font-weight: bold;
        cursor: pointer;
    }
    .rm:hover {
        opacity: 0.75;
    }
    .done {
        text-decoration: line-through;
    }
</style>