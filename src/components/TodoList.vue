<template>
  <ul class="List">
    <TodoItem v-for="todo in todos" :key="todo.id" :todo="todo" @remove-todo="removeTodo" @change-completed="changeCompleted" />
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

<style lang="scss">
$completedColor: #d6d9dd;

.List {
  padding: 0 3rem;
  overflow: scroll;
  margin-bottom: 1rem;

  p {
    padding: 0 3rem;
  }

  li {
    padding: 1rem 0;
    display: flex;
    align-items: center;

    span {
      flex: 1;
    }

    svg {
      font-size: 2rem;
      color: $completedColor;
    }
  }
  .completed {
    color: $completedColor;
    svg {
      color: #80e1ac;
    }
  }
}
</style>
