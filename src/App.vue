<template>
  <div class="container">
    <!-- Vue Components are used with a Capital letter to differentiate them from normal HTML tags -->
    <Header title="Task Tracker" />
    <!-- Since we are passing in a dynamic array we want to "v-bind" Tasks to the tasks data array  -->
    <Tasks :tasks="tasks" />
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";

export default {
  name: "App",
  components: {
    Header,
    Tasks,
  },
  data() {
    return {
      tasks: [],
    };
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
