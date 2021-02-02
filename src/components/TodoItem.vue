<template>
    <div v-bind:class="{completed: todo.completed}">
        <input type="checkbox" v-on:change="completed">
        <h4>{{ todo.title }}</h4>
        <button  @click="$emit('delete-todo', todo.id)">x</button>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ['todo'],
    data() {
        return {

        }
    },
    methods: {
        completed() {
            this.todo.completed = !this.todo.completed;
            console.log('completed');
        },
    }
}
</script>

<style scoped>
    .completed {
        background-color: aquamarine;
    }
</style>