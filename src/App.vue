<template>
  <div id="app">
    <img src="./assets/logo.png" alt />
    <h1>Vue Todos</h1>
    <TodoForm
      v-bind:isEditing="isEditing"
      v-on:clear="clearCompleted"
      v-on:add="addTodo"
      v-bind:currentTodo="currentTodo"
      v-on:update="updateTodo"
    />
    <TodoList v-bind:todos="todos" v-on:edit="toggleEdit" />
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
  methods: {
    clearCompleted: function() {
      this.todos = this.todos.filter(todo => !todo.completed);
    },
    addTodo: function(newTodo) {
      this.todos = [newTodo, ...this.todos];
    },
    toggleEdit: function(id) {
      this.isEditing = !this.isEditing;
      this.todos = this.todos.map(todo => {
        if (todo.id === id) {
          this.currentTodo = todo;
          return todo;
        } else {
          return todo;
        }
      });
    },
    updateTodo: function(updatedTodo) {
      this.todos = this.todos.map(todo => {
        if (todo.id === updatedTodo.id) {
          return {
            ...todo,
            todo: updatedTodo.todo
          };
        } else {
          return todo;
        }
      });
    }
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
          completed: true
        },
        {
          todo: "And Another",
          id: 3,
          completed: false
        }
      ],
      isEditing: false,
      currentTodo: ""
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
