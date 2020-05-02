<template>
  <div>
    <p>{{todo.todo}}</p>
  </div>
</template>

<script>
export default {
  name: "Todo",
  props: ["todo"]
};
</script>

<style>
</style>