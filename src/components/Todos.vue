<template>
    <div>
        <table class="table">
            <thead>
                <tr>
                    <th scope="col"></th>
                    <th scope="col">Id</th>
                    <th scope="col">Title</th>
                    <th scope="col">Completed</th>
                    <th scope="col">Action</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="todo in todos" :key="todo.index" v-bind:class="{completed: todo.completed}">
                    <td><input type="checkbox" v-on:change="completed(todo)"></td>
                    <td>{{ todo.id }}</td>
                    <td>{{ todo.title }}</td>
                    <td>{{ todo.completed }}</td>
                    <td><button  @click="$emit('del-todo', todo.id)">x</button></td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: "Todos",
    props: ['todos'],
    components: {
       
    },
    methods: {
        completed(todo) {
            todo.completed = !todo.completed;
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