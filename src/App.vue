<template>
  <div class="container">
    <!-- Vue Components are used with a Capital letter to differentiate them from normal HTML tags -->
    <Header @toggle-add-task="toggleAddTask" title="Task Tracker" :showAddTask="showAddTask" />
    <div v-if="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <!-- Since we are passing in a dynamic array we want to "v-bind" Tasks to the tasks data array  -->
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask";

export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
    deleteTask(id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },

    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => (task.id === id ? { ...task, reminder: !task.reminder } : task));
    },
  },
  created() {
    // This is where we tipically would put in a data request so that it can load when the page opens
    // In this case we need to create a Tasks component so we can render this info on the page
    this.tasks = [
      {
        id: 1,
        text: "Race suit fitting",
        day: "March 21st at 3:00pm",
        reminder: true,
      },
      {
        id: 2,
        text: "Mugello Free Practice",
        day: "May 23rd at 10:00am",
        reminder: true,
      },
      {
        id: 3,
        text: "Portimao Tests",
        day: "Junee 25th at 11:00am",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
