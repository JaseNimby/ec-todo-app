<template>
  <li class="todo-item">
    <input type="checkbox" v-model="checked" v-on:input="chekTodo" />
    <p>{{ todoData.content }}</p>
    <button>X</button>
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
</style>