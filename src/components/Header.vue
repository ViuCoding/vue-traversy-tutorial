<template>
  <header>
    <h1>{{ title }}</h1>
    <!-- We can pass "Props" as attributes. text and color are Props, we need to define them in the component itself -->
    <Button @btn-click="$emit('toggle-add-task')" :text="showAddTask ? 'Close' : 'Add Task'" :color="showAddTask ? 'red' : 'green'" />
    <!-- <Button text="Add Task 2" color="#5784BA" /> -->
    <!-- <Button text="Add Task 3" color="lime" /> -->
  </header>
</template>

<script>
import Button from "./Button";

export default {
  name: "Header",
  props: {
    // We can define Props as Object or as an Array
    title: String,
    showAddTask: Boolean,
  },
  // props: ["title"],
  components: { Button },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-content: center;
  margin-bottom: 20px;
}
</style>
