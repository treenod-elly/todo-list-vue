<template>
  <div className="CreateButton">
    <div>
      <span>+</span>
    </div>
    <!-- <div onClick={() => setIsShow(true)}>+</div> -->
    <TodoInput v-if="false" @add-todo="addTodo" />
  </div>
</template>

<script>
import TodoInput from "./TodoInput.vue"

export default {
  name: "TodoCreate",
  components: { TodoInput },
  props: {
    addTodo: Function,
  },
}
</script>

<style lang="scss">
@import "@//styles/util.scss";

.CreateButton {
  position: absolute;
  bottom: -2.5rem;
  text-align: center;
  line-height: 5.5rem;
  color: $greenFont;
  font-size: 2.5rem;
  width: 100%;
  cursor: pointer;
  div {
    width: 5.5rem;
    border-radius: 50%;
    background: $green;
    margin: 0 auto;

    span {
      color: white;
    }
  }
}
</style>
