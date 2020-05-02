<template>
  <div id="app">
    <img src="./assets/logo.png" alt />
    <h1>Vue Todos</h1>
    <TodoForm />
    <TodoList v-bind:todos="todos" />
  </div>
</template>

<script>
import TodoForm from "./components/TodoForm";
import TodoList from "./components/TodoList";

export default {
  name: "App",
  components: {
    TodoForm,
    TodoList
  },
  data() {
    return {
      todos: [
        {
          todo: "Todo Title",
          id: 1,
          completed: false
        },
        {
          todo: "Another Title",
          id: 2,
          completed: false
        },
        {
          todo: "And Another",
          id: 3,
          completed: false
        }
      ]
    };
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
