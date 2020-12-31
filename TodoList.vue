<template>
  <div class="wrapper">
    <p>Du har {{ left }} saker kvar att göra</p>
    <div>
      <ul class="toDoList"></ul>
    </div>
    <input v-model="newContent" placeholder="Vad behöver du få gjort?" />
    <ToDoItem
      v-for="todo in todos"
      v-bind:key="todo.id"
      v-bind:todoData="todo"
      v-on:check="checkTodo(todo)"
      v-on:remove="removeTodo(todo)"
    >
      Lägg till i listan
    </ToDoItem>
  </div>
</template>



<script>
import TodoItem from "/.TodoItem";

export default {
  components: { TodoItem },
  data() {
    return {
      newContent: "",
      todos: [],
      left: "",
    };
  },

  methods: {
    addToDo() {
      const newTodo = {
        id: Date.now(),
        content: this.newContent,
        done: false,
      };
      this.todos.push(newTodo);
    },

    checkTodo(theTodo) {
      theTodo.done = this.todo.filter((todo) => todo.id != theTodo.id);
    },

    removeTodo(tehTodo) {
      tehTodo.done = !theTodo.done;
    },
  },
};
</script>

<style scoped>
.wrapper {
  display: grid;
  grid-template-rows: 0.2fr 0.2fr;
}

p {
  max-width: 300px;
  font-size: 25px;
  margin-left: 40px;
  align-items: center;
}

ul {
  list-style: none;
  max-width: 300px;
}

li {
  background-color: lightgrey;
  padding: 0.5rem;
  cursor: pointer;
}
li:nth-of-type(2n) {
  background-color: #eee;
}

button {
  max-width: 300px;
  font-size: 25px;
  margin-left: 40px;
}

input {
  max-width: 250px;
  font-size: 15px;
  margin-left: 40px;
  margin-bottom: 10px;
}

.completed {
  text-decoration: line-through;
}
</style>