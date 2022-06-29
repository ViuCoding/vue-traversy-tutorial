<!-- What we want to do here is:
1. Take in a Prop of task (an array) and then loop through it and then output each task as a single component on screen-->

<template>
  <div :key="task.id" v-for="task in tasks">
    <!-- Since the data is still one level above we use emit once again to pass it over -->
    <Task @toggle-reminder="$emit('toggle-reminder', task.id)" @delete-task="$emit('delete-task', task.id)" :task="task" />
  </div>
</template>

<script>
import Task from "./Task.vue";

export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  components: {
    Task,
  },
  emits: ["delete-task", "toggle-reminder"],
};
</script>
