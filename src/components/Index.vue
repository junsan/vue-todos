<template>
  <div id="app">
    <Todos v-bind:todos="todos" @del-todo="delTodo" />
    <AddTodo @add-item="addItem" />
  </div>
</template>

<script>
import Todos from '../components/Todos.vue'
import AddTodo from '../components/AddTodo.vue'
import axios from 'axios'

export default {
  name: 'App',
  data() {
    return {
      todos: []
    }
  },
  methods: {
    addItem(item) {
      axios.post('http://jsonplaceholder.typicode.com/posts', {
            title: item,
            completed: false
        })
        .then(response => {
            this.todos.push(response.data)
            console.log(response.data);
        });
    },
    delTodo(id) {
      this.todos = this.todos.filter(item => item.id !== id);
      console.log("deleted");
    } 
  },
  created() {
      axios.get(`http://jsonplaceholder.typicode.com/todos?_limit=5`)
        .then(response => this.todos = response.data)
        .catch(error => console.log(error));
  },
  components: {
    Todos,
    AddTodo
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
