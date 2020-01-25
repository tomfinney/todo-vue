<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <div class>
      <button class="ui basic blue button" v-on:click="showForm" v-show="!adding">Add a todo</button>
      <button class="ui basic blue button" v-on:click="hideForm" v-show="adding">Cancel</button>
    </div>
    <add v-show="adding" v-on:add-todo="addTodo"></add>
    <todo
      v-show="!adding"
      v-for="(todo, index) in todos"
      v-bind:todo="todo"
      v-bind:key="todo.key"
      v-bind:index="index"
      v-on:delete-todo="deleteTodo"
      v-on:done-todo="doneTodo"
    ></todo>
  </div>
</template>

<script type = "text/javascript" >
import Todo from "./Todo";
import Add from "./Add";
export default {
  props: ["todos"],
  components: {
    Todo,
    Add
  },
  data() {
    return {
      adding: false
    };
  },
  methods: {
    addTodo(todo) {
      this.adding = false;
      let key =
        this.todos.length > 0 ? this.todos[this.todos.length - 1].key + 1 : 1;
      this.todos.push({ ...todo, key, done: false });
    },
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    doneTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
    },
    showForm() {
      this.adding = true;
    },
    hideForm() {
      this.adding = false;
    }
  }
};
</script>

<style>
.card {
  background-color: #f5f5f5;
  border-radius: 4px;
  max-width: 300px;
  margin: 8px auto 0;
  padding: 16px;
  text-align: left;
}
.header {
  margin: 0 0 4px;
  flex: 1;
}
.meta {
  margin: 0;
}
.controls {
  display: flex;
}
button + button {
  margin-left: 4px;
}
label {
  display: block;
  margin-bottom: 4px;
}
.field {
  margin-top: 8px;
}

.field + button {
  margin-top: 8px;
}

input,
textarea {
  width: 100%;
  border: 1px solid #e5e5e5;
  border-radius: 4px;
  padding: 8px;
}
</style>