<template>
    <li>
        <span v-bind:class="{ done: todo.completed }">
            <input
                type="checkbox"
                v-on:change="todo.completed = !todo.completed"
                :checked="todo.completed"
            />
            <strong>{{ index + 1 }}</strong>
            {{ todo.title | uppercase }}
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
        index: Number,
    },
    filters: {
        uppercase(value) {
            return value.toUpperCase();
        },
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
    align-items: center;
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
    width: 24px;
    height: 24px;
    line-height: 20px;
}
.rm:hover {
    opacity: 0.75;
}
.done {
    text-decoration: line-through;
}
</style>
