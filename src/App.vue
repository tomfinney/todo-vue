<template>
  <div id="asd">
    <h1>todos</h1>
    <todo-list v-bind:todos="todos"></todo-list>
  </div>
</template>

<script>
import TodoList from "./TodoList";

export default {
  name: "app",
  components: {
    TodoList
  },
  data() {
    return {
      todos: [
        {
          key: 1,
          title: "Todo A",
          project: "Project A",
          done: false,
          body: "do this soon"
        },
        {
          key: 2,
          title: "Todo B",
          project: "Project B",
          done: true,
          body: "do this now"
        },
        {
          key: 3,
          title: "Todo C",
          project: "Project C",
          done: false,
          body: "do this whenver"
        }
      ]
    };
  }
};
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}
#asd {
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
