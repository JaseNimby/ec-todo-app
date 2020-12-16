<template>
  <div class="wrapper">
    <p>Du har {{ left }} saker kvar att göra</p>
    <div>
      <ul class="toDoList">
        <TodoItem />
      </ul>
    </div>
    <input v-model="thing" placeholder="Vad behöver du få gjort?" />
    <button v-on:click="addToDo(thing)">Lägg till i listan</button>
  </div>
</template>



<script>
import TodItem from "./TodoItem";
export default {
  components: { TodoItem },
  data() {
    return {
      newContent: "",
      todos: [],
      left: 0,
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