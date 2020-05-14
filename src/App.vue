<template>
  <div id="app">
    <Header/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    <AddTodo v-on:add-todo="addTodo"/>
  </div>
</template>

<script>
import Todos from "./components/Todos";
import Header from "./components/layout/Header";
import AddTodo from "./components/AddTodo";

export default {
  name: "app",

  components: {
    Header,
    Todos,
    AddTodo
  },

  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Task One",
          completed: false
        },
        {
          id: 2,
          title: "Task Two",
          completed: false
        },
        {
          id: 3,
          title: "Task Three",
          completed: false
        }
      ]
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #ffffff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
