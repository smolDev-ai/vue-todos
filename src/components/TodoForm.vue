<template>
  <form @submit.prevent="update" v-if="this.isEditing">
    <input type="text" name="todo" v-model="todo" :placeholder="this.currentTodo.todo" />
    <button type="submit">Edit Todo</button>
    <button @click.prevent="$emit('clear')">Clear Completed</button>
  </form>
  <form @submit.prevent="create" v-else>
    <input type="text" name="todo" v-model="todo" placeholder="...todo" />
    <button type="submit">Add Todo</button>
    <button @click.prevent="$emit('clear')">Clear Completed</button>
  </form>
</template>

<script>
export default {
  name: "TodoForm",
  props: ["isEditing", "currentTodo"],
  data() {
    return {
      todo: this.currentTodo.todo
    };
  },
  methods: {
    create: function() {
      const newTodo = {
        todo: this.todo,
        id: Date.now(),
        completed: false
      };

      this.$emit("add", newTodo);
      this.todo = "";
    },
    update: function() {
      const updatedTodo = {
        ...this.currentTodo,
        todo: this.todo
      };
      this.$emit("update", updatedTodo);
      this.todo = "";
    }
  }
};
</script>

<style>
</style>