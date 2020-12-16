<template>
  <li class="todo-item">
    <input type="checkbox" v-model="checked" v-on:input="chekTodo" />
    <p>{{ thing }}</p>
  </li>
</template>

<script>
export default {
  props: {
    todoData: object,
  },

  methods: {
    addTodo() {
      const newTodo = {
        id: Date.now(),
        content: this.newContent,
        done: false,
        visible: true,
      };
      this.todos.push(newTodo);
      this.newContent = "";
      this.todosToBeDone += 1;
    },

    removeTodo(theTodo) {
      this.todos = this.todos.filter((todo) => todo.id != theTodo.id);
    },

    checkTodo(theTodo) {
      theTodo.done = !theTodo.done;
      if (theTodo.done) {
        this.todosToBeDone -= 1;
      } else {
        this.todosToBeDone += 1;
      }
    },
  },
};
</script>

<style scoped>
</style>