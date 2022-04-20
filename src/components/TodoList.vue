<template>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <TodoItem :todo="todo" @remove-todo="removeTodo" @change-completed="changeCompleted" />
    </li>
  </ul>
</template>

<script>
import TodoItem from "./TodoItem.vue"

export default {
  name: "TodoList",
  props: {
    todos: Array,
    removeTodo: Function,
    changeCompleted: Function,
  },
  components: {
    TodoItem,
  },
}
</script>
