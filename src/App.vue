<template>
  <div id="app">
    <AppHeader @search="search" />
    <Todos :todos="this.todos" @deltodo="deltodo" />
  </div>
</template>

<script>
import AppHeader from "./components/nav/Appheader";
import Todos from "./components/todos";
import axios from "axios";
import shortid from "shortid";

export default {
  name: "App",
  components: {
    AppHeader,
    Todos
  },
  data() {
    return {
      todos: []
    };
  },
  created() {
    axios.get("https://jsonplaceholder.typicode.com/todos").then(res => {
      const data = res.data.slice(0, 10);
      this.todos = data;
    });
  },
  methods: {
    search(e) {
      const newtodo = {
        id: shortid.generate(),
        title: e,
        completed: false
      };
      this.todos = [newtodo, ...this.todos];
    },
    deltodo(grabedid) {
      this.todos = this.todos.filter(todo => todo.id !== grabedid);
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Roboto", sans-serif;
}
</style>
