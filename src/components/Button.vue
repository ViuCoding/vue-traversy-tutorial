<!-- This is basically a blue print of a Vue component. We define here the different "Props" that we pass later as HTML attributes whenever we are using this component -->

<template>
  <!-- There are 2 ways to add click Events to a component. 
1. @click="function()"
2. v-on:click="function()"

We then need to add the method/function in the export as an object

-->
  <button @click="onClick()" :style="{ background: color }" class="btn">{{ text }}</button>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: String,
    color: String,
  },
  methods: {
    onClick() {
      this.$emit("btn-click");
    },
  },
};
</script>
