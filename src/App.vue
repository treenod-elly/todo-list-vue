<template>
  <div class="logo">
    <img alt="Vue logo" src="./assets/logo.png" />
  </div>
  <TodoDate />
  <TodoList :todos="todos" :removeTodo="removeTodo" :changeCompleted="changeCompleted" />
  <TodoCreate :addTodo="addTodo" />
</template>

<script>
import TodoList from "./components/TodoList.vue"
import TodoDate from "./components/TodoDate.vue"
import TodoCreate from "./components/TodoCreate.vue"
import axios from "axios"

export default {
  name: "App",
  components: {
    TodoList,
    TodoDate,
    TodoCreate,
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
    const res = await axios.get("https://jsonplaceholder.typicode.com/todos?userId=1")
    this.todos = res.data
  },
  methods: {
    addTodo(todo) {
      this.todos.push({ id: this.todos.length + 1, title: todo, completed: false })
    },
    removeTodo(id) {
      this.todos = this.todos.filter((v) => id !== v.id)
    },
    changeCompleted(id) {
      this.todos = this.todos.map((v) => (v.id === id ? { ...v, completed: !v.completed } : v))
    },
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: content-box;
}
body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans",
    "Helvetica Neue", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: #f0efe9;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
#app {
  color: #7b7e84;
  font-weight: bold;
  background: white;
  border: 3px solid #eaeae6;
  padding: 3rem 0;
  height: 70vh;
  min-width: 400px;
  display: flex;
  flex-direction: column;
  position: relative;
}
.logo {
  display: flex;
  justify-content: center;
}
img {
  width: 50px;
}
ul {
  list-style: none;
}
</style>
