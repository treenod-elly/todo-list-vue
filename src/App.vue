<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <TodoInput @add-todo="addTodo" />
  <TodoList :todos="todos" :removeTodo="removeTodo" :changeCompleted="changeCompleted" />
</template>

<script>
import TodoInput from "./components/TodoInput.vue"
import TodoList from "./components/TodoList.vue"
import axios from 'axios';

export default {
  name: "App",
  components: {
    TodoInput,
    TodoList,
  },
  data() {
    return {
      todos: [
        // { id: 1, title: "todo1", completed: true },
        // { id: 2, title: "todo2", completed: false },
      ],
    }
  },
  async mounted() {
    const res = await axios.get('https://jsonplaceholder.typicode.com/todos?userId=1')
    this.todos = res.data
  },
  methods: {
    addTodo(todo) {
      this.todos.push({ id: this.todos.length, title: todo, completed: false })
    },
    removeTodo(id) {
      this.todos = this.todos.filter(v => id !== v.id)
    },
    changeCompleted(id) {
      this.todos = this.todos.map((v) => (v.id === id ? { ...v, completed: !v.completed } : v))
    },
  },
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
