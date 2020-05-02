<template>
  <form @submit.prevent="create">
    <input type="text" name="todo" v-model="todo" placeholder="...todo" />
    <button type="submit">Add Todo</button>
    <button @click.prevent="$emit('clear')">Clear Completed</button>
  </form>
</template>

<script>
export default {
  name: "TodoForm",
  data() {
    return {
      todo: ""
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
    }
  }
};
</script>

<style>
</style>