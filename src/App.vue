<template>
  <div id="app">
    <h1>To-Do-List</h1>
    <form id="form" v-on:submit.prevent="saveNewTask">
      <label for="new-task">Add a new task:</label>
      <input id="new-task" type="text" v-model="newTask" required />
      <input type="submit" value="Save New Task" />
    </form>
    <div id="radio">
      <input
        type="radio"
        id="high"
        name="priority"
        v-bind:value="true"
        v-model="isPriority"
      />
      <label for="high">Urgent</label>
      <br />
      <input
        type="radio"
        id="low"
        name="priority"
        v-bind:value="false"
        v-model="isPriority"
      />
      <label for="low">No Hurry</label>
    </div>

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
  background-color: #f5f5f5;
  width: 600px;
  height: max-content;
  margin: 0 auto;
  padding: 0;
  font-family: "Caveat Brush", sans-serif;
  box-shadow: 5px 5px 16px -6px #000000;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
  border-left: 3px double #ffaa9f;
  margin-left: 40px;
}

.lines {
  border-left: 1px solid #ffaa9f;
  border-right: 1px solid #ffaa9f;
  height: 400px;
  width: 2px;
  float: left;
  margin-left: 40px;
}

li.low {
  font-size: 25px;
  color: #1a681e;
  padding: 10px;
  margin: 15px;
  list-style: none;
  border-bottom: 1px dotted #ccc;
  text-indent: 25px;
  height: auto;
  padding: 10px;
  text-transform: capitalize;
}

li.high {
  font-size: 25px;
  color: red;
  -webkit-text-stroke: 1px darkred;
  padding: 10px;
  margin: 15px;
  border-bottom: 1px dotted #ccc;
  text-indent: 25px;
  height: auto;
  padding: 10px;
  text-transform: capitalize;
  text-shadow: 0 -1px 4px #fff, 0 -2px 10px #ff0, 0 -10px 20px #ff8000,
    0 -18px 40px #f00;
}

#radio {
  display: flex;
  justify-content: center;
  padding: 10px;
}

#form {
  font-size: 20px;
  display: flex;
  justify-content: space-evenly;
  padding: 10px;
  vertical-align: middle;
}

h1 {
  display: flex;
  justify-content: center;
  color: darkblue;
}

input[type="text"] {
  width: 50%;
}

/* button,
input[type="submit"] {
  background: #000;
  color: #fff;
  cursor: pointer;
  border: 1px solid #000;
} */
</style>