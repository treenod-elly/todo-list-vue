<template>
  <div>
    <input type="text" v-model="todo"/>
    <button @click="addTodo">add</button>
  </div>
</template>

<script>
export default {
  name: "TodoInput",
  props: {},
  methods: {
    addTodo() {
      this.$emit('add-todo', this.todo)
      this.todo = ''
    }
  },
  data() {
    return {
      todo: '',
    }
  }
}
</script>

<style></style>
