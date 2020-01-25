<template>
  <div class="card">
    <div class="controls">
      <h4 class="header">{{ todo.key }} {{ todo.title }}</h4>
      <button class="edit" v-on:click="showForm">edit</button>
      <button class="remove" v-on:click="deleteTodo(todo)">remove</button>
      <button class="done" v-show="!todo.done" v-on:click="doneTodo(todo)">done</button>
    </div>
    <h5 class="meta">
      {{ todo.project }}
      <small v-show="todo.done" disabled>Completed</small>
      <small v-show="!todo.done">Pending</small>
    </h5>
    <p style="margin: 10px 0 0" v-show="!isEditing">{{ todo.body }}</p>
    <div class="content" v-show="isEditing">
      <div class="form">
        <div class="field">
          <label>Title</label>
          <input type="text" v-model="todo.title" />
        </div>
        <div class="field">
          <label>Project</label>
          <input type="text" v-model="todo.project" />
        </div>
        <div class="field">
          <label>Body</label>
          <textarea type="text" v-model="todo.hideFormbody" />
        </div>
        <button class="button" v-on:click="hideForm">Close X</button>
      </div>
    </div>
  </div>
</template>

<script type = "text/javascript" >
export default {
  props: ["todo", "index"],
  data() {
    return {
      isEditing: false
    };
  },
  methods: {
    deleteTodo(todo) {
      this.$emit("delete-todo", todo);
    },
    doneTodo(todo) {
      this.$emit("done-todo", todo);
    },
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    }
  }
};
</script>

<style>
</style>