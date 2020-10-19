<template>
  <div id="app">
    <h1>To-Do-List</h1>
    <form v-on:submit.prevent="saveNewTask">
      <label for="new-task">Add a new task:</label>
      <input id="new-task" type="text" v-model="newTask" required />
      <input type="submit" value="Save New Task" />
    </form>
    <ul>
      <li v-for="task in tasks">
        <span>{{ task.name }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [
        { name: "Clean Bathroom", isDone: false },
        { name: "Ironing", isDone: false },
        { name: "Wash Floor", isDone: true },
      ],
      newTask: "",
    };
  },
  methods: {
    saveNewTask: function () {
      this.tasks.push({ name: this.newTask, isDone: false });
      this.newTask = "";
    },
  },
};
</script>

<style>
</style>