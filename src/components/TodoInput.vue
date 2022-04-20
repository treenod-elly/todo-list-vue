<template>
  <div className="TodoCreate">
    <div className="modal">
      <div>
        <input type="text" v-model="todo" />
      </div>
      <button id="add" @click="addTodo">Add</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoInput",
  props: {},
  methods: {
    addTodo() {
      this.$emit("add-todo", this.todo)
      this.todo = ""
    },
  },
  data() {
    return {
      todo: "",
    }
  },
}
</script>

<style></style>
