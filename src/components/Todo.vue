<template>
  <div class="todo" v-bind:class="{'isCompleted': todo.completed}">
    <h2 v-on:click="completeTodo">{{todo.todo}}</h2>
    <button v-on:click="$emit('edit', todo.id)">Edit</button>
  </div>
</template>

<script>
export default {
  name: "Todo",
  props: ["todo"],
  methods: {
    completeTodo: function() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.todo {
  margin: 0 auto;
  background-color: #f3f3f3;
  width: 400px;
  height: 100px;
  border-bottom: 1px solid #3e3e3e;
}

@keyframes background-animation {
  from {
    background-color: #f3f3f3;
  }
  to {
    background-color: #f33d;
  }
}

@keyframes text-animation {
  from {
    color: #3e3e3e;
  }
  to {
    color: #fefe;
  }
}

.isCompleted {
  animation: background-animation 2s forwards;
}

.isCompleted h2 {
  text-decoration: line-through;
  animation: text-animation 3s forwards;
}
</style>