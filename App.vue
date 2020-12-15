<template>
  <div class="wrapper">
    <p>Du har {{ left }} saker kvar att göra</p>
    <div>
      <ul class="toDoList">
        <li v-for="(thing, index) in toDoList" v-bind:key="index">
          <input
            type="checkbox"
            v-model="checked"
            v-on:click="markComplete()"
          />
          {{ thing }}
        </li>
      </ul>
    </div>
    <input v-model="thing" placeholder="Vad behöver du få gjort?" />
    <button v-on:click="addToDo(thing)">Lägg till i listan</button>
  </div>
</template>



<script>
export default {
  props: ["add"],

  data() {
    return {
      toDoList: [],
      left: 0,
      thing: [],
      checked: false,
    };
  },

  methods: {
    addToDo(thing) {
      this.toDoList.push(thing), this.left++;
    },

    markComplete() {
      this.add.completed = !this.add.completed;
      this.left--;
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





























<!-- <template>
  <div id="app">
    <div>Du har {{ left }} saker kvar</div> 
    <List v-bind:list="list" />
    <Button v-on:add-todo="addTodo" />
  </div>
</template>
<script>
import List from "./List";
import Button from "./Button";
export default {
  name: "app",
  components: {
    List,
    Button,
  },
  data() {
    return {
      left: 0,
      list: [
        {
          id: 1,
          title: "Go workout",
          completed: false,
        },
        {
          id: 2,
          title: "Do laundry",
          completed: false,
        },
        {
          id: 3,
          title: "Cook food",
          completed: false,
        },
      ],
    };
  },
  methods: {
    addTodo(newTodoObj) {
      this.list.push(newTodoObj), this.left++;
    },
  },
};
</script>
<style>
</style>-->