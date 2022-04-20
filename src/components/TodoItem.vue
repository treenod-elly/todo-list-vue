<template>
  <li @dblclick="this.$emit('remove-todo', todo.id)">
    <span>{{ todo.title }}</span>
    <input type="checkbox" name="" id="" @click="this.$emit('change-completed', todo.id)" :checked="todo.completed" />
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
