<template>
  <div class="wrapper">
    <p>Du har {{ todosToBeDone }} saker kvar att göra</p>
    <div>
      <ul class="toDoList">
        <TodoItem
          v-for="todo in todos"
          v-bind:key="todo.id"
          v-bind:todoData="todo"
          v-on:check="checkTable(todo)"
        />
      </ul>
    </div>
    <input v-model="newContent" placeholder="Vad behöver du få gjort?" />
    <button v-on:click="addTodo(newContent)">Lägg till i listan</button>
  </div>
</template>



<script>
import TodoItem from "./TodoItem";
export default {
  components: { TodoItem },
  data() {
    return {
      newContent: "",
      todos: [],
      todosToBeDone: 0,
    };
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