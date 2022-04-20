<template>
  <li>
    <input type="checkbox" name="" id="" @click="this.$emit('change-completed', todo.id)" :checked="todo.completed" />
    <span>{{ todo.title }}</span>
    <button @click="this.$emit('remove-todo', todo.id)">X</button>
  </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todo: Object,
  },
}
</script>

<style></style>
