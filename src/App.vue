<template>
  <div id="app">
    <h1>To-Do-List</h1>
    <form v-on:submit.prevent="saveNewTask">
      <label for="new-task">Add a new task:</label>
      <input id="new-task" type="text" v-model="newTask" required />
      <input type="submit" value="Save New Task" />
    </form>
    <input
      type="radio"
      id="high"
      name="priority"
      v-bind:value="true"
      v-model="isPriority"
    />
    <label for="one">High</label>
    <br />
    <input
      type="radio"
      id="low"
      name="priority"
      v-bind:value="false"
      v-model="isPriority"
    />
    <label for="two">Low</label>

    <ul>
      <li v-for="task in tasks" v-bind:class="task.isPriority ? 'high' : 'low'">
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
        { name: "Clean Bathroom", isPriority: false },
        { name: "Ironing", isPriority: false },
        { name: "Wash Floor", isPriority: true },
      ],
      newTask: "",
    };
  },
  methods: {
    saveNewTask: function () {
      this.tasks.push({ name: this.newTask, isPriority: this.isPriority });
      this.newTask = "";
    },
  },
};
</script>

<style>
#app {
  width: 50%;
  margin: 0 auto;
  font-family: "Courier", sans-serif;
}

li.low {
  border: 2px solid #1a681e;
  color: #1a681e;
}

li.high {
  border: 2px solid #f2360c;
  color: #f2360c;
}
</style>