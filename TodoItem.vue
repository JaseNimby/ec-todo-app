<template>
  <li class="todo-item">
    <input type="checkbox" v-on:input="checkTodo" />
    <p>{{ todoData.content }}</p>
    <button v-on:click="removeTodo">X</button>
  </li>
</template>

<script>
export default {
  props: {
    todoData: Object,
  },

  methods: {
    checkTodo() {
      this.$emit("check");
    },

    deleteTodo() {
      this.$emit("delete");
    },
  },
};
</script>

<style scoped>
.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: lightgray;
}
.todo-item > p {
  width: 100%;
}
.todo-item > * {
  padding: 0.25rem;
  margin: 0.25rem;
}
</style>