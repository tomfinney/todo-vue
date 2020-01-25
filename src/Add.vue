<template>
  <div class="card">
    <h4 class="header">New Todo</h4>
    <div class="form">
      <div class="field">
        <label>Title</label>
        <input type="text" v-model="title" />
        <div v-show="!!errors.title">{{ `title ${errors.title}`}}</div>
      </div>
      <div class="field">
        <label>Project</label>
        <input type="text" v-model="project" />
        <div v-show="!!errors.project">{{ `project ${errors.project}`}}</div>
      </div>
      <div class="field">
        <label>Body</label>
        <textarea type="text" v-model="body" />
        <div v-show="!!errors.body">{{ `body ${errors.body}`}}</div>
      </div>
      <button class="button" v-on:click="addTodo">Submit</button>
    </div>
  </div>
</template>

<script type = "text/javascript" >
export default {
  data() {
    return {
      title: "",
      project: "",
      body: "",
      errors: {}
    };
  },
  methods: {
    addTodo() {
      this.errors = {};

      let payload = {
        title: this.title,
        project: this.project,
        body: this.body
      };

      let valid = true;

      for (let key in payload) {
        if (!payload[key]) {
          valid = false;
          this.errors[key] = "must be present";
        }
      }

      if (valid) {
        this.$emit("add-todo", payload);
        this.title = "";
        this.project = "";
        this.body = "";
      }
    }
  }
};
</script>

<style>
</style>